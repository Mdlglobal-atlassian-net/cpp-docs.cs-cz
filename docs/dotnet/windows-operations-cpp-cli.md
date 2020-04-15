---
title: Operace systému Windows (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371776"
---
# <a name="windows-operations-ccli"></a>Operace systému Windows (C++/CLI)

Ukazuje různé úlohy specifické pro systém Windows pomocí sady Windows SDK.

Následující témata ukazují různé operace systému Windows prováděné se sadou Windows SDK pomocí sady Visual C++.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>Zjištění, zda bylo spuštěno vypnutí

Následující příklad kódu ukazuje, jak zjistit, zda je aktuálně ukončována aplikace nebo rozhraní .NET Framework. To je užitečné pro přístup ke statickým prvkům v rozhraní .NET Framework, protože během vypnutí jsou tyto konstrukce dokončeny systémem a nelze je spolehlivě použít. Kontrolou vlastnosti <xref:System.Environment.HasShutdownStarted%2A> jako první, můžete se vyhnout potenciální selhání tím, že přístup k těmto prvkům.

### <a name="example"></a>Příklad

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>Určení interaktivního stavu uživatele

Následující příklad kódu ukazuje, jak zjistit, zda je kód spuštěn v kontextu interaktivní uživatele. Pokud <xref:System.Environment.UserInteractive%2A> je false, pak je kód spuštěn jako proces služby nebo z evnitř webové aplikace, v takovém případě byste se neměli pokoušet o interakci s uživatelem.

### <a name="example"></a>Příklad

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>Čtení dat z registru systému Windows

Následující příklad kódu <xref:Microsoft.Win32.Registry.CurrentUser> používá klíč ke čtení dat z registru systému Windows. Nejprve jsou podklíče uvedeny pomocí <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metody a potom je pomocí <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody otevřen podklíč Identities. Stejně jako kořenové klíče je <xref:Microsoft.Win32.RegistryKey> každý podklíč reprezentován třídou. Nakonec nový <xref:Microsoft.Win32.RegistryKey> objekt se používá k výčet dvojice klíč/hodnota.

### <a name="example"></a>Příklad

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>Poznámky

Třída <xref:Microsoft.Win32.Registry> je pouze kontejner pro statické <xref:Microsoft.Win32.RegistryKey>instance . Každá instance představuje kořenový uzel registru. Instance <xref:Microsoft.Win32.Registry.ClassesRoot>jsou , <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, a .

Kromě statické, objekty v <xref:Microsoft.Win32.Registry> rámci třídy jsou jen pro čtení. Kromě toho instance <xref:Microsoft.Win32.RegistryKey> třídy, které jsou vytvořeny pro přístup k obsahu objektů registru jsou také jen pro čtení. Příklad, jak přepsat toto chování, naleznete v [tématu How to: Write Data to the Windows Registry (C++/CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

Ve třídě <xref:Microsoft.Win32.Registry> existují dva další objekty: <xref:Microsoft.Win32.Registry.DynData> a <xref:Microsoft.Win32.Registry.PerformanceData>. Oba jsou instance <xref:Microsoft.Win32.RegistryKey> třídy. Objekt <xref:Microsoft.Win32.Registry.DynData> obsahuje informace o dynamickém registru, které jsou podporovány pouze v systémech Windows 98 a Windows ME. Objekt <xref:Microsoft.Win32.Registry.PerformanceData> lze použít pro přístup k informacím čítače výkonu pro aplikace, které používají systém sledování výkonu systému Windows. Uzel <xref:Microsoft.Win32.Registry.PerformanceData> představuje informace, které nejsou ve skutečnosti uloženy v registru a proto nelze zobrazit pomocí Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>Čtení čítačů výkonu systému Windows

Některé aplikace a podsystémy systému Windows zveřejňují údaje o výkonu prostřednictvím systému výkonu systému Windows. Tyto čítače lze <xref:System.Diagnostics.PerformanceCounterCategory> přistupovat pomocí a <xref:System.Diagnostics.PerformanceCounter> třídy, které jsou umístěny <xref:System.Diagnostics?displayProperty=fullName> v oboru názvů.

Následující příklad kódu používá tyto třídy k načtení a zobrazení čítače, který je aktualizován systémem Windows k označení procenta času, který je procesor zaneprázdněn.

> [!NOTE]
> Tento příklad vyžaduje oprávnění správce ke spuštění v systému Windows Vista.

### <a name="example"></a>Příklad

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>Načtení textu ze schránky

Následující příklad kódu <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> používá členská funkce k <xref:System.Windows.Forms.IDataObject> vrácení ukazatele do rozhraní. Toto rozhraní pak může být dotazován na formát dat a slouží k načtení skutečných dat.

### <a name="example"></a>Příklad

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>Načíst aktuální uživatelské jméno

Následující příklad kódu ukazuje načtení aktuálního uživatelského jména (jméno uživatele přihlášeného k systému Windows). Název je uložen <xref:System.Environment.UserName%2A> v řetězci, který <xref:System.Environment> je definován v oboru názvů.

### <a name="example"></a>Příklad

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>Načíst verzi rozhraní .NET Framework

Následující příklad kódu ukazuje, jak určit verzi aktuálně nainstalované rozhraní <xref:System.Environment.Version%2A> .NET Framework s <xref:System.Version> vlastností, což je ukazatel na objekt, který obsahuje informace o verzi.

### <a name="example"></a>Příklad

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>Načíst název místního počítače

Následující příklad kódu ukazuje načtení názvu místního počítače (název počítače tak, jak je zobrazen v síti). Toho lze dosáhnout získáním <xref:System.Environment.MachineName%2A> řetězce, který <xref:System.Environment> je definován v oboru názvů.

### <a name="example"></a>Příklad

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>Načtení verze systému Windows

Následující příklad kódu ukazuje, jak načíst informace o platformě a verzi aktuálního operačního systému. Tyto informace jsou <xref:System.Environment.OSVersion%2A?displayProperty=fullName> uloženy ve vlastnosti a skládá se z výčtu, <xref:System.Environment.Version%2A> který popisuje verzi systému Windows v širokém slova smyslu a objekt, který obsahuje přesné sestavení operačního systému.

### <a name="example"></a>Příklad

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>Načíst čas uplynulý od spuštění

Následující příklad kódu ukazuje, jak určit počet značek nebo počet milisekund, které uplynuly od spuštění systému Windows. Tato hodnota je <xref:System.Environment.TickCount%2A?displayProperty=fullName> uložena v členu a protože se jedná o 32bitovou hodnotu, obnoví se přibližně každých 24,9 dne na nulu.

### <a name="example"></a>Příklad

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>Uložení textu do schránky

Následující příklad kódu <xref:System.Windows.Forms.Clipboard> používá objekt <xref:System.Windows.Forms> definovaný v oboru názvů k uložení řetězce. Tento objekt poskytuje dvě <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>členské funkce: a . Data jsou uložena ve schránce odesláním <xref:System.Object> <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>libovolného objektu odvozeného do aplikace .

### <a name="example"></a>Příklad

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>Zápis dat do registru systému Windows

Následující příklad kódu <xref:Microsoft.Win32.Registry.CurrentUser> používá klíč k vytvoření zapisovatelné instance <xref:Microsoft.Win32.RegistryKey> třídy odpovídající klíči **Software.** Metoda <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> se pak používá k vytvoření nového klíče a přidání do párů klíč/hodnota.

### <a name="example"></a>Příklad

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>Poznámky

Rozhraní .NET Framework můžete použít pro <xref:Microsoft.Win32.Registry> přístup <xref:Microsoft.Win32.RegistryKey> k registru s třídami a, které jsou definovány <xref:Microsoft.Win32> v oboru názvů. Třída **Registry** je kontejner pro statické <xref:Microsoft.Win32.RegistryKey> instance třídy. Každá instance představuje kořenový uzel registru. Instance <xref:Microsoft.Win32.Registry.ClassesRoot>jsou , <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, a .

## <a name="related-sections"></a>Související oddíly

<xref:System.Environment>

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
