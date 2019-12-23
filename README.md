# HideDriver
之前那份是7600的，每次编译搞得好麻烦。更新一个VS2017可以直接编译的。


Simple way:

typedef struct _DriverSection
{
	LIST_ENTRY listentry;
}DriverSection;

// in DriverEntry
DriverSection* ds = DriverObject->DriverSection;
if (ds) {
  ds->listentry.Blink->Flink = ds->listentry.Flink;
  ds->listentry.Flink->Blink= ds->listentry.Blink;
  InitializeListHead(&ds->listentry);
}
