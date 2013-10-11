cmake_minimum_required(VERSION 2.8)

project(ode)

# Include necessary submodules
#set(CMAKE_MODULE_PATH
#	"${iRobot_SOURCE_DIR}/CMake"
#	"${iRobot_SOURCE_DIR}/CMake/Utils"
#	"${iRobot_SOURCE_DIR}/CMake/Packages"
#	"${iRobot_SOURCE_DIR}/CMake/Templates"
#)

set(HEADER_FILES 
	include/ode/collision.h
	include/ode/collision_space.h
	include/ode/collision_trimesh.h
	include/ode/common.h
	include/ode/compatibility.h
	include/ode/contact.h
	include/ode/error.h
	include/ode/export-dif.h
	include/ode/mass.h
	include/ode/matrix.h
	include/ode/memory.h
	include/ode/misc.h
	include/ode/objects.h
	include/ode/ode.h
	include/ode/odeconfig.h
	include/ode/odecpp.h
	include/ode/odecpp_collision.h
	include/ode/odeinit.h
	include/ode/odemath_legacy.h
	include/ode/rotation.h
	include/ode/timer.h
	ode/src/joints/universal.h
	ode/src/joints/slider.h
	ode/src/joints/pu.h
	ode/src/joints/pr.h
	ode/src/joints/plane2d.h
	ode/src/joints/piston.h
	ode/src/joints/null.h
	ode/src/joints/lmotor.h
	ode/src/joints/joints.h
	ode/src/joints/joint_internal.h
	ode/src/joints/joint.h
	ode/src/joints/hinge2.h
	ode/src/joints/hinge.h
	ode/src/joints/fixed.h
	ode/src/joints/contact.h
	ode/src/joints/amotor.h	
	libccd/src/ccd/alloc.h
	libccd/src/ccd/ccd.h
	libccd/src/ccd/compiler.h
	libccd/src/ccd/dbg.h
	libccd/src/ccd/list.h
	libccd/src/ccd/polytope.h
	libccd/src/ccd/quat.h
	libccd/src/ccd/simplex.h
	libccd/src/ccd/support.h
	libccd/src/ccd/vec3.h
	ode/src/config.h
	)
	
set(SOURCE_FILES 
	ode/src/fastdot.c
	ode/src/fastldlt.c
	ode/src/fastlsolve.c
	ode/src/fastltsolve.c
	ode/src/nextafterf.c
	ode/src/array.cpp
	ode/src/box.cpp
	ode/src/capsule.cpp
	ode/src/collision_cylinder_box.cpp
	ode/src/collision_cylinder_plane.cpp
	ode/src/collision_cylinder_sphere.cpp
	ode/src/collision_cylinder_trimesh.cpp
	ode/src/collision_kernel.cpp
	ode/src/collision_quadtreespace.cpp
	ode/src/collision_sapspace.cpp
	ode/src/collision_space.cpp
	ode/src/collision_transform.cpp
	ode/src/collision_trimesh_box.cpp
	ode/src/collision_trimesh_ccylinder.cpp
	ode/src/collision_trimesh_disabled.cpp
	ode/src/collision_trimesh_distance.cpp
	ode/src/collision_trimesh_gimpact.cpp
	ode/src/collision_trimesh_opcode.cpp
	ode/src/collision_trimesh_plane.cpp
	ode/src/collision_trimesh_ray.cpp
	ode/src/collision_trimesh_sphere.cpp
	ode/src/collision_trimesh_trimesh.cpp
	ode/src/collision_trimesh_trimesh_new.cpp
	ode/src/collision_util.cpp
	ode/src/collision_libccd.cpp
	ode/src/convex.cpp
	ode/src/cylinder.cpp
	ode/src/error.cpp
	ode/src/export-dif.cpp
	ode/src/heightfield.cpp
	ode/src/lcp.cpp
	ode/src/mass.cpp
	ode/src/mat.cpp
	ode/src/matrix.cpp
	ode/src/memory.cpp
	ode/src/misc.cpp
	ode/src/obstack.cpp
	ode/src/ode.cpp
	ode/src/odeinit.cpp
	ode/src/odemath.cpp
	ode/src/odeou.cpp
	ode/src/odetls.cpp
	ode/src/plane.cpp
	ode/src/quickstep.cpp
	ode/src/ray.cpp
	ode/src/rotation.cpp
	ode/src/sphere.cpp
	ode/src/step.cpp
	ode/src/timer.cpp
	ode/src/util.cpp
	libccd/src/alloc.c
	libccd/src/ccd.c
	libccd/src/mpr.c
	libccd/src/polytope.c
	libccd/src/support.c
	libccd/src/vec3.c
	OPCODE/OPC_AABBCollider.cpp
	OPCODE/OPC_AABBTree.cpp
	OPCODE/OPC_BaseModel.cpp
	OPCODE/OPC_Collider.cpp
	OPCODE/OPC_Common.cpp
	OPCODE/OPC_HybridModel.cpp
	OPCODE/OPC_LSSCollider.cpp
	OPCODE/OPC_MeshInterface.cpp
	OPCODE/OPC_Model.cpp
	OPCODE/OPC_OBBCollider.cpp
	OPCODE/OPC_OptimizedTree.cpp
	OPCODE/OPC_Picking.cpp
	OPCODE/OPC_PlanesCollider.cpp
	OPCODE/OPC_RayCollider.cpp
	OPCODE/OPC_SphereCollider.cpp
	OPCODE/OPC_TreeBuilders.cpp
	OPCODE/OPC_TreeCollider.cpp
	OPCODE/OPC_VolumeCollider.cpp
	OPCODE/Opcode.cpp	
	ode/src/joints/amotor.cpp
	ode/src/joints/ball.cpp
	ode/src/joints/contact.cpp
	ode/src/joints/fixed.cpp
	ode/src/joints/hinge.cpp
	ode/src/joints/hinge2.cpp
	ode/src/joints/joint.cpp
	ode/src/joints/lmotor.cpp
	ode/src/joints/null.cpp
	ode/src/joints/piston.cpp
	ode/src/joints/plane2d.cpp
	ode/src/joints/pr.cpp
	ode/src/joints/pu.cpp
	ode/src/joints/slider.cpp
	ode/src/joints/universal.cpp	
	OPCODE/Ice/IceAABB.cpp
	OPCODE/Ice/IceContainer.cpp
	OPCODE/Ice/IceHPoint.cpp
	OPCODE/Ice/IceIndexedTriangle.cpp
	OPCODE/Ice/IceMatrix3x3.cpp
	OPCODE/Ice/IceMatrix4x4.cpp
	OPCODE/Ice/IceOBB.cpp
	OPCODE/Ice/IcePlane.cpp
	OPCODE/Ice/IcePoint.cpp
	OPCODE/Ice/IceRandom.cpp
	OPCODE/Ice/IceRay.cpp
	OPCODE/Ice/IceRevisitedRadix.cpp
	OPCODE/Ice/IceSegment.cpp
	OPCODE/Ice/IceTriangle.cpp
	OPCODE/Ice/IceUtils.cpp		
	)
	
	SOURCE_GROUP("Source Files" FILES
	)
	
	SOURCE_GROUP("Source Files\\Joint" FILES
	ode/src/joints/amotor.cpp
	ode/src/joints/ball.cpp
	ode/src/joints/contact.cpp
	ode/src/joints/fixed.cpp
	ode/src/joints/hinge.cpp
	ode/src/joints/hinge2.cpp
	ode/src/joints/joint.cpp
	ode/src/joints/lmotor.cpp
	ode/src/joints/null.cpp
	ode/src/joints/piston.cpp
	ode/src/joints/plane2d.cpp
	ode/src/joints/pr.cpp
	ode/src/joints/pu.cpp
	ode/src/joints/slider.cpp
	ode/src/joints/universal.cpp
	)

	SOURCE_GROUP("Source Files\\Ice" FILES
	OPCODE/Ice/IceAABB.cpp
	OPCODE/Ice/IceContainer.cpp
	OPCODE/Ice/IceHPoint.cpp
	OPCODE/Ice/IceIndexedTriangle.cpp
	OPCODE/Ice/IceMatrix3x3.cpp
	OPCODE/Ice/IceMatrix4x4.cpp
	OPCODE/Ice/IceOBB.cpp
	OPCODE/Ice/IcePlane.cpp
	OPCODE/Ice/IcePoint.cpp
	OPCODE/Ice/IceRandom.cpp
	OPCODE/Ice/IceRay.cpp
	OPCODE/Ice/IceRevisitedRadix.cpp
	OPCODE/Ice/IceSegment.cpp
	OPCODE/Ice/IceTriangle.cpp
	OPCODE/Ice/IceUtils.cpp	
	)
	
	SOURCE_GROUP("Source Files\\OPCODE" FILES
	OPCODE/OPC_AABBCollider.cpp
	OPCODE/OPC_AABBTree.cpp
	OPCODE/OPC_BaseModel.cpp
	OPCODE/OPC_Collider.cpp
	OPCODE/OPC_Common.cpp
	OPCODE/OPC_HybridModel.cpp
	OPCODE/OPC_LSSCollider.cpp
	OPCODE/OPC_MeshInterface.cpp
	OPCODE/OPC_Model.cpp
	OPCODE/OPC_OBBCollider.cpp
	OPCODE/OPC_OptimizedTree.cpp
	OPCODE/OPC_Picking.cpp
	OPCODE/OPC_PlanesCollider.cpp
	OPCODE/OPC_RayCollider.cpp
	OPCODE/OPC_SphereCollider.cpp
	OPCODE/OPC_TreeBuilders.cpp
	OPCODE/OPC_TreeCollider.cpp
	OPCODE/OPC_VolumeCollider.cpp
	OPCODE/Opcode.cpp	
	)
	
	SOURCE_GROUP("Header Files" FILES
	)
	
	SOURCE_GROUP("Header Files\\Joints" FILES
	ode/src/joints/universal.h
	ode/src/joints/slider.h
	ode/src/joints/pu.h
	ode/src/joints/pr.h
	ode/src/joints/plane2d.h
	ode/src/joints/piston.h
	ode/src/joints/null.h
	ode/src/joints/lmotor.h
	ode/src/joints/joints.h
	ode/src/joints/joint_internal.h
	ode/src/joints/joint.h
	ode/src/joints/hinge2.h
	ode/src/joints/hinge.h
	ode/src/joints/fixed.h
	ode/src/joints/contact.h
	ode/src/joints/amotor.h	
	)
	
# Specify build paths
set(ode_WORK_DIR ${ode_BINARY_DIR})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${ode_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${ode_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${ode_BINARY_DIR}/bin)

add_definitions("/DdDOUBLE")
add_definitions("/DCCD_DOUBLE")
add_definitions("/DdLIBCCD_CYL_CYL")
add_definitions("/DdLIBCCD_ENABLED")

include_directories(
include
ode/src
ode/src/joints
opcode
ou/include
GIMPACT/include
ou/include
libccd/src
)

if (WIN32)
	add_definitions("/DODE_DLL")
	add_library(ode SHARED ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCE_FILES})
elseif(APPLE)
	add_definitions("/DODE_LIB")
	add_library(ode STATIC ${HEADER_FILES} ${SOURCE_FILES} ${RESOURCE_FILES})
endif ()


