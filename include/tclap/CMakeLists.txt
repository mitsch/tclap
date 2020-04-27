
set(HEADER_FILES
        ArgContainer.h
        ArgException.h
        ArgGroup.h
        Arg.h
        ArgTraits.h
        CmdLine.h
        CmdLineInterface.h
        CmdLineOutput.h
        Constraint.h
        DeferDelete.h
        DocBookOutput.h
        HelpVisitor.h
        IgnoreRestVisitor.h
        MultiArg.h
        MultiSwitchArg.h
        OptionalUnlabeledTracker.h
        sstream.h
        StandardTraits.h
        StdOutput.h
        SwitchArg.h
        UnlabeledMultiArg.h
        UnlabeledValueArg.h
        ValueArg.h
        ValuesConstraint.h
        VersionVisitor.h
        Visitor.h
)

#target_sources(TCLAP INTERFACE ${HEADER_FILES})
install(FILES ${HEADER_FILES} DESTINATION include/tclap)
