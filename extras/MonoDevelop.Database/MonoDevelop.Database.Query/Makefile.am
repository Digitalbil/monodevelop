ADDIN_BUILD = $(top_builddir)/build
ASSEMBLY = $(ADDIN_BUILD)/MonoDevelop.Database.Query.dll
REFS =  \
	$(GLIB_SHARP_LIBS) \
	$(GTK_SHARP_LIBS) \
	$(MONO_ADDINS_LIBS) \
	$(MONODEVELOP_CORE_ADDINS_LIBS) \
	$(MONODEVELOP_LIBS) \
	-r:$(top_builddir)/build/MonoDevelop.Database.Components.dll \
	-r:$(top_builddir)/build/MonoDevelop.Database.Sql.dll \
	-r:Mono.Posix \
	-r:System \
	-r:System.Data

RES =  \
	gtk-gui/gui.stetic \
	MonoDevelop.Database.Query.addin.xml

FILES =  \
	AssemblyInfo.cs \
	Commands/ToolCommands.cs \
	gtk-gui/generated.cs \
	ISqlQueryEditorView.cs \
	QueryResultView.cs \
	SqlQueryDisplayBinding.cs \
	SqlQueryTextEditorExtension.cs \
	SqlQueryView.cs

DATA_FILES =  \
	icons/Icons.16x16.Database.Column.Key.png \
	icons/Icons.16x16.Database.Column.png \
	icons/Icons.16x16.Database.Connection.Error.png \
	icons/Icons.16x16.Database.Connection.png \
	icons/Icons.16x16.Database.Connection.Remove.png \
	icons/Icons.16x16.Database.Constraints.png \
	icons/Icons.16x16.Database.Database.Error.png \
	icons/Icons.16x16.Database.Database.Ok.png \
	icons/Icons.16x16.Database.Database.png \
	icons/Icons.16x16.Database.Execute.png \
	icons/Icons.16x16.Database.Function.png \
	icons/Icons.16x16.Database.Parameter.png \
	icons/Icons.16x16.Database.Procedure.Error.png \
	icons/Icons.16x16.Database.Procedure.png \
	icons/Icons.16x16.Database.Procedure.Source.png \
	icons/Icons.16x16.Database.Relations.png \
	icons/Icons.16x16.Database.Table.Error.png \
	icons/Icons.16x16.Database.Table.png \
	icons/Icons.16x16.Database.Tables.png \
	icons/Icons.16x16.Database.User.png \
	icons/Icons.16x16.Database.Users.png \
	icons/Icons.16x16.Database.View.Error.png \
	icons/Icons.16x16.Database.View.png \
	icons/Icons.16x16.Database.View.Source.png \
	icons/Icons.16x16.Database.Views.png

DATA_FILE_BUILD = $(addprefix $(ADDIN_BUILD)/, $(DATA_FILES))

all: $(ASSEMBLY)

$(ASSEMBLY): $(build_sources) $(build_resources)
	mkdir -p $(ADDIN_BUILD)
	$(CSC) $(CSC_FLAGS) $(REFS) $(build_resources:%=/resource:%) $(build_sources) -out:$@ -target:library

$(DATA_FILE_BUILD): $(srcdir)$(subst $(ADDIN_BUILD),, $@)
	mkdir -p $(dir $@)
	cp $(srcdir)/$(subst $(ADDIN_BUILD),,$@) $@


assemblydir = $(MD_ADDIN_DIR)/MonoDevelop.Database
assembly_DATA = $(ASSEMBLY) $(ASSEMBLY).mdb

iconsdir = $(MD_ADDIN_DIR)/MonoDevelop.Database/icons
icons_DATA = $(DATA_FILE_BUILD)

CLEANFILES = $(ASSEMBLY) $(ASSEMBLY).mdb $(DATA_FILE_BUILD)
EXTRA_DIST = $(FILES) $(RES) $(DATA_FILES)

include $(top_srcdir)/Makefile.include
