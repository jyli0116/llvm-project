lldb_tablegen(TraceExporterCTFCommandOptions.inc -gen-lldb-option-defs
  SOURCE TraceExporterCTFOptions.td
  TARGET TraceExporterCTFOptionsGen)

add_lldb_library(lldbPluginTraceExporterCTF PLUGIN
CommandObjectThreadTraceExportCTF.cpp
  TraceExporterCTF.cpp

  LINK_COMPONENTS
    Support
  LINK_LIBS
    lldbCore
    lldbSymbol
    lldbTarget
    lldbPluginTraceExporterCommon
  )

add_dependencies(lldbPluginTraceExporterCTF TraceExporterCTFOptionsGen)
