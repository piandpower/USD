set(PXR_PREFIX pxr/imaging)
set(PXR_PACKAGE hd)

set(optionalPublicClasses "")

if (OPENSUBDIV_HAS_GLSL_TRANSFORM_FEEDBACK)
    add_definitions(-DOPENSUBDIV_HAS_GLSL_TRANSFORM_FEEDBACK)
endif()
if (OPENSUBDIV_HAS_GLSL_COMPUTE)
    add_definitions(-DOPENSUBDIV_HAS_GLSL_COMPUTE)
endif()

pxr_shared_library(hd
    LIBRARIES
        plug
        tf
        tracelite
        vt
        work
        sdf
        garch
        hf
        glf
        pxOsd
        ${OPENSUBDIV_LIBRARIES}
        ${GLEW_LIBRARY}
        ${TBB_tbb_LIBRARY}

    INCLUDE_DIRS
        ${OPENSUBDIV_INCLUDE_DIR}
        ${GLEW_INCLUDE_DIR}
        ${TBB_INCLUDE_DIRS}
        ${OPENSUBDIV_INCLUDE_DIR}

    PUBLIC_CLASSES
        basisCurves
        basisCurvesTopology
        binding
        bprim
        bufferArray
        bufferArrayRange
        bufferArrayRegistry
        bufferResource
        bufferSource
        bufferSpec
        changeTracker
        codeGen
        commandBuffer
        computation
        conversions
        copyComputation
        debugCodes
        dirtyList
        dispatchBuffer
        drawingCoord
        drawBatch
        drawItem
        drawItemInstance
        drawItemState
        engine
        fallbackLightingShader
        geometricShader
        glslProgram
        glslfxShader
        glUtils
        immediateDrawBatch
        indirectDrawBatch
        instancer
        instanceRegistry
        interleavedMemoryManager
        lightingShader
        mesh
        meshTopology
        meshUtil
        package
        patchIndex
        perfLog
        persistentBuffer
        points
        primTypeIndex
        renderContextCaps
        renderDelegate
        renderIndex
        renderPass
        renderPassShader
        renderPassState
        repr
        resource
        resourceBinder
        resourceRegistry
        rprim
        rprimCollection
        rprimSharedData
        sceneDelegate
        shader
        shaderCode
        shaderKey
        shaderParam
        smoothNormals
        sprim
        strategyBase
        surfaceShader
        task
        texture
        textureResource
        tokens
        topology
        unitTestDelegate
        unitTestGLDrawing
        vboMemoryManager
        vboSimpleMemoryManager
        vertexAdjacency
        vtBufferSource

    PUBLIC_HEADERS
        api.h
        enums.h
        types.h
        version.h

    PRIVATE_CLASSES
        cullingShaderKey
        unitTestHelper
        unitTestNullRenderDelegate
        ${optionalPrivateClasses}

    RESOURCE_FILES
        plugInfo.json
        shaders/basisCurves.glslfx
        shaders/compute.glslfx
        shaders/fallbackLighting.glslfx
        shaders/fallbackLightingShader.glslfx
        shaders/fallbackSurface.glslfx
        shaders/frustumCull.glslfx
        shaders/instancing.glslfx
        shaders/mesh.glslfx
        shaders/meshNormal.glslfx
        shaders/meshWire.glslfx
        shaders/points.glslfx
        shaders/ptexTexture.glslfx
        shaders/renderPass.glslfx
        shaders/renderPassShader.glslfx
)

