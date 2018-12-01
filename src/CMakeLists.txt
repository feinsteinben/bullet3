
IF(BUILD_BULLET3)
        SUBDIRS(  Bullet3OpenCL Bullet3Serialize/Bullet2FileLoader Bullet3Dynamics Bullet3Collision Bullet3Geometry )
ENDIF(BUILD_BULLET3)


SUBDIRS(   BulletInverseDynamics BulletSoftBody BulletCollision BulletDynamics LinearMath Bullet3Common)


IF(INSTALL_LIBS)
        #INSTALL of other files requires CMake 2.6
        IF (${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 2.5)
                IF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
                        # Don't actually need to install any common files, the frameworks include everything
                ELSE (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
                        INSTALL(FILES btBulletCollisionCommon.h btBulletDynamicsCommon.h  DESTINATION ${INCLUDE_INSTALL_DIR})
                ENDIF (APPLE AND BUILD_SHARED_LIBS AND FRAMEWORK)
        ENDIF (${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION} GREATER 2.5)
ENDIF(INSTALL_LIBS)



INCLUDE_DIRECTORIES(
                ${BULLET_PHYSICS_SOURCE_DIR}/src
                ${BULLET_PHYSICS_SOURCE_DIR}/examples
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/glad
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/openvr/headers
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/openvr/samples/shared
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/enet/include
                ${BULLET_PHYSICS_SOURCE_DIR}/examples/ThirdPartyLibs/clsocket/src
                ${PYTHON_INCLUDE_DIRS}
)

SET(c_api_SRCS
	../../examples/SharedMemory/plugins/collisionFilterPlugin/collisionFilterPlugin.cpp
	../../examples/SharedMemory/plugins/collisionFilterPlugin/collisionFilterPlugin.h
	../../examples/SharedMemory/plugins/pdControlPlugin/pdControlPlugin.cpp
	../../examples/SharedMemory/plugins/pdControlPlugin/pdControlPlugin.h
	../../examples/SharedMemory/b3RobotSimulatorClientAPI_NoDirect.cpp
	../../examples/SharedMemory/b3RobotSimulatorClientAPI_NoDirect.h
	../../examples/SharedMemory/IKTrajectoryHelper.cpp
	../../examples/SharedMemory/IKTrajectoryHelper.h
	../../examples/SharedMemory/PhysicsClient.cpp
	../../examples/SharedMemory/PhysicsClientSharedMemory.cpp
	../../examples/SharedMemory/PhysicsServerExample.cpp
	../../examples/SharedMemory/PhysicsServerExampleBullet2.cpp
	../../examples/SharedMemory/PhysicsServerSharedMemory.cpp
	../../examples/SharedMemory/PhysicsServerSharedMemory.h
	../../examples/SharedMemory/PhysicsServer.cpp
	../../examples/SharedMemory/PhysicsServer.h
	../../examples/SharedMemory/PhysicsClientC_API.cpp
	../../examples/SharedMemory/SharedMemoryCommands.h
	../../examples/SharedMemory/SharedMemoryPublic.h
	../../examples/SharedMemory/PhysicsServer.cpp
	../../examples/SharedMemory/PosixSharedMemory.cpp
	../../examples/SharedMemory/Win32SharedMemory.cpp
	../../examples/SharedMemory/InProcessMemory.cpp
	../../examples/SharedMemory/PhysicsDirect.cpp
	../../examples/SharedMemory/PhysicsDirect.h
	../../examples/SharedMemory/PhysicsDirectC_API.cpp
	../../examples/SharedMemory/PhysicsDirectC_API.h
	../../examples/SharedMemory/PhysicsLoopBack.cpp
	../../examples/SharedMemory/PhysicsLoopBack.h
	../../examples/SharedMemory/PhysicsLoopBackC_API.cpp
	../../examples/SharedMemory/PhysicsLoopBackC_API.h
	../../examples/SharedMemory/PhysicsClientSharedMemory_C_API.cpp
	../../examples/SharedMemory/PhysicsClientSharedMemory_C_API.h
	../../examples/SharedMemory/PhysicsClientSharedMemory2_C_API.cpp
	../../examples/SharedMemory/PhysicsClientSharedMemory2_C_API.h
	../../examples/SharedMemory/PhysicsClientSharedMemory2.cpp
	../../examples/SharedMemory/PhysicsClientSharedMemory2.h
	../../examples/SharedMemory/SharedMemoryCommandProcessor.cpp
	../../examples/SharedMemory/SharedMemoryCommandProcessor.h
	../../examples/SharedMemory/PhysicsServerCommandProcessor.cpp
	../../examples/SharedMemory/PhysicsServerCommandProcessor.h
	../../examples/SharedMemory/plugins/tinyRendererPlugin/tinyRendererPlugin.cpp
	../../examples/SharedMemory/plugins/tinyRendererPlugin/TinyRendererVisualShapeConverter.cpp
        ../../examples/SharedMemory/SharedMemoryCommands.h
	../../examples/SharedMemory/SharedMemoryPublic.h
	../../examples/SharedMemory/b3PluginManager.cpp
	../../examples/TinyRenderer/geometry.cpp
	../../examples/TinyRenderer/model.cpp
	../../examples/TinyRenderer/tgaimage.cpp
	../../examples/TinyRenderer/our_gl.cpp
	../../examples/TinyRenderer/TinyRenderer.cpp
	../../examples/OpenGLWindow/SimpleCamera.cpp
	../../examples/OpenGLWindow/SimpleCamera.h
	../../examples/Importers/ImportURDFDemo/ConvertRigidBodies2MultiBody.h
	../../examples/Importers/ImportURDFDemo/MultiBodyCreationInterface.h
	../../examples/Importers/ImportURDFDemo/MyMultiBodyCreator.cpp
	../../examples/Importers/ImportURDFDemo/MyMultiBodyCreator.h
	../../examples/Importers/ImportURDFDemo/BulletUrdfImporter.cpp
	../../examples/Importers/ImportURDFDemo/BulletUrdfImporter.h
	../../examples/Importers/ImportURDFDemo/UrdfParser.cpp
 	../../examples/Importers/ImportURDFDemo/urdfStringSplit.cpp
	../../examples/Importers/ImportURDFDemo/UrdfParser.cpp
	../../examples/Importers/ImportURDFDemo/UrdfParser.h
	../../examples/Importers/ImportURDFDemo/URDF2Bullet.cpp
	../../examples/Importers/ImportMJCFDemo/BulletMJCFImporter.cpp
	../../examples/Importers/ImportMJCFDemo/BulletMJCFImporter.h
	../../examples/Utils/b3ResourcePath.cpp
	../../examples/Utils/b3Clock.cpp
        ../../examples/Utils/b3ERPCFMHelper.hpp
        ../../examples/Utils/b3ReferenceFrameHelper.hpp
	../../examples/Utils/RobotLoggingUtil.cpp
	../../examples/Utils/RobotLoggingUtil.h
	../../examples/Utils/ChromeTraceUtil.cpp
	../../examples/Utils/ChromeTraceUtil.h
	../../examples/Importers/ImportURDFDemo/URDFImporterInterface.h
	../../examples/Importers/ImportURDFDemo/URDFJointTypes.h
	../../examples/Importers/ImportObjDemo/Wavefront2GLInstanceGraphicsShape.cpp
	../../examples/Importers/ImportObjDemo/LoadMeshFromObj.cpp
	../../examples/Importers/ImportSTLDemo/ImportSTLSetup.h
	../../examples/Importers/ImportSTLDemo/LoadMeshFromSTL.h
	../../examples/Importers/ImportColladaDemo/LoadMeshFromCollada.cpp
	../../examples/Importers/ImportColladaDemo/ColladaGraphicsInstance.h
	../../examples/ThirdPartyLibs/Wavefront/tiny_obj_loader.cpp
	../../examples/ThirdPartyLibs/tinyxml2/tinyxml2.cpp
        ../../examples/ThirdPartyLibs/BussIK/Jacobian.cpp
        ../../examples/ThirdPartyLibs/BussIK/LinearR2.cpp
        ../../examples/ThirdPartyLibs/BussIK/LinearR3.cpp
        ../../examples/ThirdPartyLibs/BussIK/LinearR4.cpp
        ../../examples/ThirdPartyLibs/BussIK/MatrixRmn.cpp
        ../../examples/ThirdPartyLibs/BussIK/Misc.cpp
        ../../examples/ThirdPartyLibs/BussIK/Node.cpp
        ../../examples/ThirdPartyLibs/BussIK/Tree.cpp
        ../../examples/ThirdPartyLibs/BussIK/VectorRn.cpp
	../../examples/Importers/ImportMeshUtility/b3ImportMeshUtility.cpp
	../../examples/ThirdPartyLibs/stb_image/stb_image.cpp
	../../examples/MultiThreading/b3ThreadSupportInterface.cpp
	../../examples/MultiThreading/b3ThreadSupportInterface.h
        ../../examples/MultiThreading/b3PosixThreadSupport.cpp
        ../../examples/MultiThreading/b3Win32ThreadSupport.cpp
        ../../Extras/InverseDynamics/btMultiBodyTreeCreator.cpp
        ../../Extras/InverseDynamics/CloneTreeCreator.cpp
        ../../Extras/InverseDynamics/CoilCreator.cpp
        ../../Extras/InverseDynamics/DillCreator.cpp
        ../../Extras/InverseDynamics/IDRandomUtil.cpp
        ../../Extras/InverseDynamics/invdyn_bullet_comparison.cpp
        ../../Extras/InverseDynamics/MultiBodyNameMap.cpp
        ../../Extras/InverseDynamics/MultiBodyTreeCreator.cpp
        ../../Extras/InverseDynamics/MultiBodyTreeDebugGraph.cpp
        ../../Extras/InverseDynamics/RandomTreeCreator.cpp
        ../../Extras/InverseDynamics/SimpleTreeCreator.cpp
        ../../Extras/InverseDynamics/User2InternalIndex.cpp
        ../../Extras/Serialize/BulletFileLoader/bFile.cpp
        ../../Extras/Serialize/BulletFileLoader/bDNA.cpp
        ../../Extras/Serialize/BulletFileLoader/bChunk.cpp
        ../../Extras/Serialize/BulletFileLoader/btBulletFile.cpp
        ../../Extras/Serialize/BulletWorldImporter/btBulletWorldImporter.cpp
        ../../Extras/Serialize/BulletWorldImporter/btWorldImporter.cpp
)

ADD_DEFINITIONS(-DPHYSICS_SERVER_DIRECT)

ADD_LIBRARY(PhysicsClientC_API ${c_api_SRCS})

SET_TARGET_PROPERTIES(PhysicsClientC_API PROPERTIES VERSION ${BULLET_VERSION})
SET_TARGET_PROPERTIES(PhysicsClientC_API PROPERTIES SOVERSION ${BULLET_VERSION})

TARGET_LINK_LIBRARIES(PhysicsClientC_API BulletSoftBody BulletDynamics BulletCollision BulletInverseDynamics LinearMath Bullet3Common)

IF (INSTALL_LIBS)
        INSTALL(FILES
                ../examples/SharedMemory/PhysicsClientC_API.h
                ../examples/SharedMemory/PhysicsClientSharedMemory_C_API.h
                ../examples/SharedMemory/PhysicsClientSharedMemory2_C_API.h
                ../examples/SharedMemory/PhysicsDirectC_API.h
                ../examples/SharedMemory/PhysicsClientUDP_C_API.h
                ../examples/SharedMemory/SharedMemoryInProcessPhysicsC_API.h
                ../examples/SharedMemory/SharedMemoryPublic.h
                DESTINATION include/bullet
                )
        INSTALL(TARGETS
                PhysicsClientC_API
                LIBRARY DESTINATION lib${LIB_SUFFIX}
                ARCHIVE DESTINATION lib${LIB_SUFFIX}
                )
ENDIF (INSTALL_LIBS)


