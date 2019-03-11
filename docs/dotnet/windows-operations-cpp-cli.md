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
ms.openlocfilehash: 413ccc3b66d76f8779861d4d65eb262ee8640725
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750894"
---
# <a name="windows-operations-ccli"></a>Operace systému Windows (C++/CLI)

Ukazuje různé úlohy specifické pro Windows pomocí sady Windows SDK.

Následující témata ukazují různé Windows operace prováděné s Windows SDK pomocí jazyka Visual C++.

## <a name="determine_shutdown"></a> Určení, zda bylo zahájeno vypínání

Následující příklad kódu ukazuje, jak určit, zda je aktuálně ukončení aplikace nebo rozhraní .NET Framework. To je užitečné pro přístup k statických elementů v rozhraní .NET Framework, protože během vypínání tyto konstrukce jsou dokončeny v systému a není možné spolehlivě použít. Kontrolou <xref:System.Environment.HasShutdownStarted%2A> vlastnost poprvé, můžete se vyhnout potenciálních selhání přístupu k těmto prvkům.

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

## <a name="determine_user"></a> Určení interaktivního uživatelského stavu

Následující příklad kódu ukazuje, jak určit, zda kód je spuštěn v kontextu interaktivního uživatele. Pokud <xref:System.Environment.UserInteractive%2A> má hodnotu false, pak je kód spuštěn jako proces služeb nebo z webové aplikace, v takovém případě byste se neměli pokoušet k interakci s uživatelem.

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

## <a name="read_registry"></a> Čtení dat z registru Windows

Následující příklad kódu používá <xref:Microsoft.Win32.Registry.CurrentUser> klíče pro čtení dat z registru Windows. Nejprve podklíčů uvedených pomocí <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metody a poté podklíč identity je otevřen pomocí <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metoda. Podobně jako kořenového klíče, je reprezentována podklíč <xref:Microsoft.Win32.RegistryKey> třídy. Nakonec novou <xref:Microsoft.Win32.RegistryKey> objektu se používá k vytvoření výčtu páry klíč/hodnota.

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

<xref:Microsoft.Win32.Registry> Třídy slouží pouze jako kontejner pro statické instance <xref:Microsoft.Win32.RegistryKey>. Každá instance představuje kořenový uzel registru. Instance jsou <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, a <xref:Microsoft.Win32.Registry.Users>.

Navíc se statické, objekty v rámci <xref:Microsoft.Win32.Registry> třídy jsou jen pro čtení. Kromě toho instance z <xref:Microsoft.Win32.RegistryKey> třídu, která se vytváří za účelem přístupu k obsahu registru objekty a jsou jen pro čtení. Příklad toho, jak toto chování přepsat, naleznete v tématu [jak: Zápis dat do registru Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

Ve třídě <xref:Microsoft.Win32.Registry> existují dva další objekty: <xref:Microsoft.Win32.Registry.DynData> a <xref:Microsoft.Win32.Registry.PerformanceData>. Jsou obě instance <xref:Microsoft.Win32.RegistryKey> třídy. <xref:Microsoft.Win32.Registry.DynData> Obsahuje informace o dynamické registru, který je podporován pouze ve Windows 98 a Windows Me. <xref:Microsoft.Win32.Registry.PerformanceData> Objekt lze použít pro přístup k informacím čítače výkonu pro aplikace, které používají systém sledování výkonu Windows. <xref:Microsoft.Win32.Registry.PerformanceData> Informace, které nejsou ve skutečnosti uložené v registru a proto nemůže zobrazit pomocí Regedit.exe představuje uzel.

## <a name="read_performance"></a> Čtení čítačů výkonu Windows

Některé aplikace a subsystémy Windows vystavit údaje o výkonu prostřednictvím výkonu systému Windows. Tyto čítače jsou přístupné pomocí <xref:System.Diagnostics.PerformanceCounterCategory> a <xref:System.Diagnostics.PerformanceCounter> třídy, které jsou umístěny v <xref:System.Diagnostics?displayProperty=fullName> oboru názvů.

Následující příklad kódu používá tyto třídy k načtení a zobrazení čítač, který se aktualizuje pomocí Windows k označení zadaného procenta času procesoru je zaneprázdněný.

> [!NOTE]
>  Tento příklad vyžaduje oprávnění správce pro spuštění v systému Windows Vista.

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

## <a name="retrieve_text"></a> Načtení textu ze schránky

Následující příklad kódu používá <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> a vrátí ukazatel na členskou funkci <xref:System.Windows.Forms.IDataObject> rozhraní. Toto rozhraní pak jde dotazovat pro formát data a používá se k načtení skutečná data.

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

## <a name="retrieve_current"></a> Načtení aktuálního jména uživatele

Následující příklad kódu ukazuje načítání aktuální uživatelské jméno (název uživatel přihlášený Windows). Název je uložen v <xref:System.Environment.UserName%2A> řetězec, který je definován v <xref:System.Environment> oboru názvů.

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

## <a name="retrieve_dotnet"></a> Načtení verze rozhraní .NET Framework

Následující příklad kódu ukazuje, jak určit verzi aktuálně nainstalované rozhraní .NET Framework s <xref:System.Environment.Version%2A> vlastnost, která je ukazatel na <xref:System.Version> objekt, který obsahuje informace o verzi.

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

## <a name="retrieve_local"></a> Načtení názvu místního počítače

Následující příklad kódu ukazuje načtení názvu místního počítače (název počítače, protože se zobrazí v síti). Můžete to provést tím, že získáme <xref:System.Environment.MachineName%2A> řetězec, který je definován v <xref:System.Environment> oboru názvů.

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

## <a name="retrieve_version"></a> Načtení verze rozhraní Windows

Následující příklad kódu ukazuje, jak načíst informace o aktuální operační systém platformy a verzi. Tyto informace jsou uloženy v <xref:System.Environment.OSVersion%2A?displayProperty=fullName> vlastnost a skládá se z výčtu, který popisuje verzi Windows v různé podmínky a <xref:System.Environment.Version%2A> objekt, který obsahuje přesně sestavení operačního systému.

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

## <a name="retrieve_time"></a> Načtení doby uplynulé od spuštění

Následující příklad kódu ukazuje, jak určit počet impulsů nebo počet milisekund uplynulých od Windows spustil. Tato hodnota bude uložena v <xref:System.Environment.TickCount%2A?displayProperty=fullName> člena a protože je to hodnota 32-bit, resetuje na nulu přibližně každých 24.9 dnů.

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

## <a name="store_text"></a> Store textu do schránky

Následující příklad kódu používá <xref:System.Windows.Forms.Clipboard> definované v objektu <xref:System.Windows.Forms> obor názvů pro uložení řetězce. Tento objekt obsahuje dva členské funkce: <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> a <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Data jsou uložena ve schránce odesláním jakéhokoli objektu odvozeného od <xref:System.Object> k <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.

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

## <a name="write_data"></a> Zápis dat do registru Windows

Následující příklad kódu používá <xref:Microsoft.Win32.Registry.CurrentUser> klávesy vytvořte instanci zapisovat <xref:Microsoft.Win32.RegistryKey> třída odpovídající **softwaru** klíč. <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> Metody se pak použije k vytvoření nového klíče a přidejte do dvojic klíč/hodnota.

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

Můžete použít pro přístup k registru pomocí rozhraní .NET Framework <xref:Microsoft.Win32.Registry> a <xref:Microsoft.Win32.RegistryKey> třídy, které jsou definovány v <xref:Microsoft.Win32> oboru názvů. **Registru** třídy je kontejner pro statické instance <xref:Microsoft.Win32.RegistryKey> třídy. Každá instance představuje kořenový uzel registru. Instance jsou <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, a <xref:Microsoft.Win32.Registry.Users>.

## <a name="related-sections"></a>Související oddíly

<xref:System.Environment>

## <a name="see-also"></a>Viz také:

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
