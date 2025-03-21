project(Hypodermic)
cmake_minimum_required(VERSION 3.13)


set(Hypodermic_headers

    ActivatedRegistrationInfo.h
    ActivationException.h
    ActivationHandler.h
    ActivationHandlers.h
    ActivationRegistry.h
    ActivationResult.h
    AnyArgument.h
    ArgumentPack.h
    ArgumentResolver.h
    As.h
    AsSelf.h
    AutowireableConstructor.h
    AutowireableConstructorRegistrationDescriptor.h
    Behavior.h
    CircularDependencyException.h
    ComponentContext.h
    Config.h
    ConsoleLoggerSink.h
    ConstructorDescriptor.h
    ConstructorTypologyDeducer.h
    Container.h
    ContainerBuilder.h
    ContainerInstanceRegistration.h
    ContainerInstanceRegistrationActivator.h
    DependencyActivationException.h
    DependencyFactories.h
    DependencyFactory.h
    DependencyFactoryTag.h
    EnforceBaseOf.h
    EnforceDependencyNotAlreadyRegistered.h
    ExceptionBase.h
    FactoryWrapper.h
    Hypodermic.h
    ILoggerSink.h
    IMutableRegistrationScope.h
    InstanceAlreadyActivatingException.h
    InstanceFactory.h
    InstanceLifetime.h
    InstanceRegistrationTags.h
    IntegerSequence.h
    IRegistration.h
    IRegistrationActivator.h
    IRegistrationDescriptor.h
    IRegistrationRegistry.h
    IRegistrationScope.h
    IResolutionContainer.h
    IResolutionContext.h
    IRuntimeRegistrationBuilder.h
    IsComplete.h
    IsSupportedArgument.h
    ITypeAlias.h
    Log.h
    Logger.h
    LogLevel.h
    MetaContains.h
    MetaForEach.h
    MetaIdentity.h
    MetaInsert.h
    MetaMap.h
    MetaPair.h
    Named.h
    NamedTypeAlias.h
    NestedRegistrationScope.h
    NoopLoggerSink.h
    OnActivated.h
    PersistentInstanceRegistration.h
    PointerAlignment.h
    Pragmas.h
    ProvidedDependencyTag.h
    ProvidedInstanceDependencyTag.h
    ProvidedInstanceFactoryRegistrationDescriptor.h
    ProvidedInstanceRegistration.h
    ProvidedInstanceRegistrationActivator.h
    ProvidedInstanceRegistrationDescriptor.h
    Registration.h
    RegistrationActivator.h
    RegistrationBuilder.h
    RegistrationContext.h
    RegistrationDescriptorBase.h
    RegistrationDescriptorBuilder.h
    RegistrationDescriptorInfo.h
    RegistrationDescriptorInfoToString.h
    RegistrationException.h
    RegistrationScope.h
    ResolutionContainer.h
    ResolutionContext.h
    ResolutionException.h
    ResolutionInfo.h
    RuntimeRegistrationBuilder.h
    SingleInstance.h
    TypeAlias.h
    TypeAliases.h
    TypeAliasKey.h
    TypeInfo.h
    UseIfNone.h
    With.h
)

if(${HYPODERMIC_COPY_HEADER_TO_BINARY_DIR})

    file(COPY ${Hypodermic_headers} DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/include/Hypodermic)

endif()

if(NOT ${HYPODERMIC_NO_INSTALL})

    install(FILES ${Hypodermic_headers} DESTINATION include/Hypodermic)

    #########################################
    # pkgconfig
    #########################################
    set(VERSION "${HYPODERMIC_VERSION}")
    set(prefix "${CMAKE_INSTALL_PREFIX}")
    set(exec_prefix "\${prefix}")
    set(includedir "\${prefix}/include")
    configure_file(
        ${CMAKE_CURRENT_SOURCE_DIR}/libhypodermic.pc.in
        ${CMAKE_CURRENT_BINARY_DIR}/libhypodermic.pc
    @ONLY)

    install(
        FILES ${CMAKE_CURRENT_BINARY_DIR}/libhypodermic.pc
        DESTINATION lib/pkgconfig
    )

endif()
