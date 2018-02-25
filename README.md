# T-SPLINE
T-SPLINE Library.
Contact: xiaowenlei@buaa.edu.cn

## 1. INTRODUCTION

### 1.1 Overview

T-SPLINE -- A T-spline object oriented package in C++
Copyright (C) 2015-  Wenlei Xiao

The T-SPLINE Library is an ***OPEN SOURCE***, ***EASY TO UNDERSTAND***, ***EASY TO COMPILE***, and ***EASY TO USE*** C++ package for T-spline.

This library is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 3.0 of the
License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

Report problems and direct all questions to:

Wenlei Xiao, Associate Professor<br>
School of Mechanical Engineering and Automation<br>
Beihang University<br>
D-315, New Main Building, <br>
Beijing, P.R. China, 100191<br>

email: xiaowenlei@buaa.edu.cn

### 1.2 History & Credits

Developing History:
- 2015.03: Wenlei Xiao started the project;
- 2016.01: Wenlei Xiao released the first version of T-SPLINE Library;
- 2016.01: Yazui Liu joined the team;
- 2016.03: Yazui Liu rewrite the rhino tsm parser from matlab to c++;
- 2016.04: Wenlei Xiao and Yazui Liu added projects: tsm2stl, tsm2obj, tsm2dxf and tsm2stp;
- 2016.04: Oleksandr Zavalnyi joined the team;
- 2016.05: Oleksandr Zavalnyi added projects: tsm2gpl and viewer;
- 2016.06: Yazui Liu added OpenMP to support more efficient tessellation;
- 2016.10: Wenlei Xiao and Yazui Liu added the analytical and matrix forms of basis functions;
- 2016.10: Lorenz Lechner from TU Graz, Austria added the python bindings;
- 2016.10: Yazui Liu and Oleksandr Zavalnyi rewrite the viewer using GLC Player;
- 2016.12: Wenlei Xiao suggested and Yazui Liu developed the Matrix-like mesh data structure;
- 2017.02: Oleksandr Zavalnyi developed the Andriod viewer for T-SPLINE (https://github.com/RubykoAlex/T-spline-android-viewer);
- 2017.02: Jia Zhang joined the team;
- 2017.11: Xinjie Zhang joined the team;
- 2018.02: Xinjie Zhang rewrite the tessellator;

Acknowledgements:

T-SPLINE has been developed for more than one year. Beside the developers, I wish to thank and acknowledge the contributions of the following group of people:
- Gang Zhao: He helped to define the terms of new data structures and promoted the idea of T-mapper.
- Rui Li: He gave many advices on the T-spline thoery during the development;
- Wei Wang: He had the first discussion with me on the efficiency and complexity of T-spline;

### 1.3 Citation

It is recommended to cite our article, if the source code can help you:

Reconsideration of T-spline data models and their exchanges using STEP. Computer-Aided Design, 2016, 79, 36-47.

	@article{Xiao201636,
	title = "Reconsideration of T-spline data models and their exchanges using \{STEP\} ",
	journal = "Computer-Aided Design ",
	volume = "79",
	number = "",
	pages = "36 - 47",
	year = "2016",
	note = "",
	issn = "0010-4485",
	doi = "http://dx.doi.org/10.1016/j.cad.2016.06.004",
	url = "http://www.sciencedirect.com/science/article/pii/S0010448516300616",
	author = "Wenlei Xiao and Yazui Liu and Rui Li and Wei Wang and Jianmin Zheng and Gang Zhao",
	keywords = "T-spline",
	keywords = "Data model",
	keywords = "STEP",
	keywords = "Data exchange "
	}

## 2. HOW TO UNDERSTAND

T-spline is a new approach to define freeform surfaces with relatively less control points than NURBS and is able to represent a model using a single surface without joining errors.
Whereas, the complexity of T-spline data models leads numerous difficulties in its programming, which hinders the research and development of T-spline technologies. 
Here, the T-SPLINE kernel gives a set of redesigned data models which have much more understanding conveniences to both human and computer. For more detail information, please refer to 
our article[1].

## 3. HOW TO BUILD

To build and compile the T-SPLINE library, CMake tools have to be used.
	
### 3.1. BUILDING on Windows systems:
	- Run CMake;
	- Specify the source code and binary directories (fill the corresponding entries with value 
	  "../SOURCE_DIRECTORY" or drag the "CMakeLists.txt" file);
	- Press Configure button, set up the Generator settings(choose the Microsoft Visual C++ (MSVC) version);
	- After configuring done few options can be chosen:
		BUILD_DOCUMENTATION (allows to generate gocumentation): <yes> <no> (Doxygen tool is required to use this option); 
		CMAKE_INSTALL_PREFIX(define the directory where "*.lib" files and header files will be generated);
		OpenMP (allows to activate multiprocessing): <yes> <no>.
	- Press Generate button(it will generate all the binary files in the SOURCE_DIRECTORY);
	- Open tspline.sln file in MSVC and build the solution;
	- To generate "*.lib" files and header files, build INSTALL project;
	- To generate documentation Doxyfile created in the SOURCE_DIRECTORY/doxy folder can be used for the Doxygen tool
		
### 3.2. BUILDING on unix/debian-like systems:
	- Run the following comands in terminal:
		$ cd SOURCE_DIRECTORY
		$ cmake .
		$ make 
			(try make -j4 for a faster build if you have a multi-core machine)
			(all "*.exe" files and "*.a" libraries will be generated in the SOURCE_DIRECTORY)
		$ sudo make install
			(will install all the header files, default directory is /usr/local/include)				
	- If you also want to build the documentation, then run:
		$ make doc
			(this should create the documentation in the SOURCE_DIRECTORY/doxy directory)

### 3.3. BUILDING on Mac systems:
	- Using Command Line: all the steps are similar to the steps described in section 2.2. BUILDING on unix/debian-like systems 
	- Using CMake software:
	- Run CMake;
	- Specify the source code and binary directories (fill the corresponding entries with value 
	  "../SOURCE_DIRECTORY" or drag the "CMakeLists.txt" file);
	- Press Configure button, set up the Generator settings(choose the Generator)			 				
	- After configuring done few options can be chosen:
		BUILD_DOCUMENTATION (allows to generate gocumentation): <yes> <no> (Doxygen tool is required to use this option); 
	- Press Generate button(it will generate all the binary files in the SOURCE_DIRECTORY)
		(if Unix Makefiles Generator has been chosen it will produce Makefile in the SOURCE_DIRECTORY and all the comands 
		described in section 2.2. BUILDING on unix/debian-like systems (except $ cmake .)have to be run in Command Line).
	- To generate documentation Doxyfile created in the SOURCE_DIRECTORY/doxy folder can be used for the Doxygen tool
		
## 4. HOW TO USE
### 4.1 DEMO
The demo project will show you how to use the T-spline kernel. It creates a mouse T-spline model and generates STL files(ASCII & BINARY), OBJ file, DXF files(T-imgage, T-connect and T-pointset), STEP file and GNUPlot files.

```cpp
//// Create a mouse T-spline model.

MouseDemoPtr demo = makePtr<MouseDemo>();

//// Get the T-spline pointer of the mouse model.
TSplinePtr spline = demo->findTSpline();

//// Construct the tessellator using T-spline pointer.
TTessellator tessellator(spline);

//// Tessellation and get all the triangle meshes.
TriMeshPtr trimesh = tessellator.interpolateAll();

//// Write a single mesh to the STL ASCII file.
StlWriter stlwriter(dirname + "/" + splinename, trimesh);
stlwriter.writeStlAcii();

ObjWriter objwriter(dirname + "/" + splinename, 0);
std::vector<std::string> faces;
demo->findTFaceNames(faces);
for (int i=0;i<faces.size();i++)
{
	//// Tessellation for every T-face seperately.
	TriMeshPtr trimesh = tessellator.interpolateFace(faces[i]);
	objwriter.addMesh(trimesh);
	//// Write every mesh to the STL BINARY file.
	StlWriter stlwriter(dirname + "/" + splinename+"-"+faces[i], trimesh);
	stlwriter.writeStlBinary();
}
//// Write a single mesh to the OBJ file.
objwriter.writeObj();
DxfWriter dxfwriter(dirname + "/" + splinename, spline);
dxfwriter.writeDxfTPointset(); //Write T-pointset to the DXF file.
dxfwriter.writeDxfTConnect(); //Write T-connect to the DXF file.
dxfwriter.writeDxfTImage(); //Write T-image to the DXF file.
StepWriter stepwriter(dirname + "/" + splinename, demo->findTGroup());
stepwriter.writeStep(); //Write T-spline model to the STEP file.
GnuplotWriter gplwriter(dirname + "/" + splinename, trimesh, spline);
gplwriter.writeGnuplMesh(); //Write T-mesh to the GNUPlot file.
gplwriter.writeGnuplTImage(); //Write T-image to the GNUPlot file.
gplwriter.writeGnuplTConnect(); //Write T-connect to the GNUPlot file.
gplwriter.writeGnuplTPointset(); //Write T-pointset to the GNUPlot file.
```
### 4.2 TSM2STL

	- Converts a TSM file to a STL ASCII/BINARY file.
	- Usage: tsm2stl.exe [*.tsm] [-asc/-bin]
	
### 4.3 TSM2OBJ

	- Converts a TSM file to an OBJ file.
	- Usage: tsm2obj.exe [*.tsm]

### 4.4 TSM2STP

	- Converts a TSM file to a STEP file.
	- Usage: tsm2stp.exe [*.tsm]

### 4.5 TSM2DXF

	- Converts a TSM file to DXF(T-imgage, T-connect and T-pointset) files.
	- Usage: tsm2dxf.exe [*.tsm] [-img/-cnt/-pst]

### 4.6 TSM2GPL

	- Converts TSM file to GNUPlot(T-mesh, T-imgage, T-connect and T-pointset) files.
	- Usage: tsm2gpl.exe [*.tsm]

### 4.7 VIEWER
	- A T-spline 3D viewer with GUI(developed using GLC Player libaries).
	
### 4.8 NOTES
	- For Windows, use '..\' to get the parent directory and use '.\' to get the current directory.
	- For Linux & MAC, use '../' to get the parent directory and use './' to get the current directory.
	
## 5. TODO LIST
* 5.1 Close T-spline has not been supported yet.
* 5.2 T-NURCCS has not been supported yet.

## Reference: 
* [1] Wenlei Xiao, Yazui Liu, Rui Li, Wei Wang, Jianmin Zheng, Gang Zhao. Reconsideration of T-spline data models and their exchanges using STEP. Computer-Aided Design, 2016, 79, 36 - 47.
