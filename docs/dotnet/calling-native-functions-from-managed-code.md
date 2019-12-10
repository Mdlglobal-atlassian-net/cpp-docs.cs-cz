---
title: Volání nativních funkcí ze spravovaného kódu
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988666"
---
# <a name="calling-native-functions-from-managed-code"></a>Volání nativních funkcí ze spravovaného kódu

Modul CLR (Common Language Runtime) poskytuje platformu vyvolání služby, jinak PInvoke, což umožňuje spravovat kód napsaný v jazyce C u volaných funkcí s nativně propojenými dynamickými knihovnami (DLL). Stejné zařazování dat se používá také u vzájemné funkční spolupráce modelu COM s modulem runtime a pro mechanismus "Prostě to funguje" nebo mechanismus IJW.

Další informace najdete v části .

- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Příklady v tomto oddíle ukazují, jak lez použít `PInvoke`. `PInvoke` umí zjednodušit vlastní zařazování dat, protože poskytnete zařazovací informace deklarativně v atributech namísto v ručně psaném kódu procesního zařazování.

> [!NOTE]
>  Zařazovací knihovna poskytuje alternativní způsob optimálního zařazování dat mezi nativními a spravovanými prostředími. Další informace o zařazovací knihovně najdete [v C++ tématu Přehled zařazování](../dotnet/overview-of-marshaling-in-cpp.md) . Knihovna zařazování je použitelná pouze pro data, ne pro funkce.

## <a name="pinvoke-and-the-dllimport-attribute"></a>Atribut PInvoke a DllImport

Následující příklad ukazuje použití `PInvoke` v programu napsaném v aplikaci Visual C++. Nativní funkce vkládání je definována v souboru msvcrt.dll. Atribut DllImport se používá pro deklaraci vkládání.

```cpp
// platform_invocation_services.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", CharSet=CharSet::Ansi)]
extern "C" int puts(String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Následující příklad je ekvivalentní k předchozímu příkladu, s rozdílem použití IJW.

```cpp
// platform_invocation_services_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <stdio.h>

int main() {
   String ^ pStr = "Hello World!";
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();
   puts(pChars);

   Marshal::FreeHGlobal((IntPtr)pChars);
}
```

### <a name="advantages-of-ijw"></a>Výhody systému souborů IJW

- Není nutné deklarovat atribut `DLLImport` pro nespravované rozhraní API, které program používá. Obsahuje pouze hlavičku souboru a spojení s importovanou knihovnou.

- Mechanismus IJW je mírně rychlejší (například zástupné procedury IJW nepotřebují kontrolovat připnuté nebo kopírované datové položky, protože to explicitně provádí vývojář).

- To jasně ukazuje problémy s výkonem. V tomto případě fakt, že provádíte převod Unicode řetězce na řetězec ANSI a máte přidělení a odebrání dodatečné paměti. V tomto případě by vývojář píšící kód s pomocí IJW zjistil, že volání `_putws` a použití `PtrToStringChars` by bylo lepší pro výkon.

- Pokud voláte mnoho nespravovaných API rozhraní používajících stejná data, je provedení jednoho zařazení a předání zařazené kopie mnohem efektivnější než provádění zařazení vždy znovu.

### <a name="disadvantages-of-ijw"></a>Nevýhody systému souborů IJW

- Zařazování musí být zadané explicitně přímo v kódu namísto pomocí atributů (které mají často vhodné výchozí nastavení).

- Kód zařazování je vložen tam, kde je v toku aplikační logiky invazivnější.

- Protože explicitní zařazování rozhraní API vrací typy `IntPtr` pro přenositelnost z 32bitové na 64bitovou verzi, musíte použít další volání `ToPointer`.

Konkrétní metoda použitá v jazyce C++ je efektivnější, explicitní metoda, která má na druhou stranu některé další složitosti.

Pokud aplikace používá převážně nespravované datové typy nebo pokud volá více nespravované rozhraní API než rozhraní API .NET Framework, doporučujeme použití funkce IJW. Příležitostné volání nespravovaného API rozhraní ve většině spravovaných aplikacích je složitější.

## <a name="pinvoke-with-windows-apis"></a>PInvoke pomocí rozhraní API systému Windows

PInvoke je vhodné pro volání funkcí v systému Windows.

V tomto příkladu spolupracuje program Visual C++ s funkcí MessageBox, která je součástí rozhraní API systému Win32.

```cpp
// platform_invocation_services_4.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
typedef void* HWND;
[DllImport("user32", CharSet=CharSet::Ansi)]
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);

int main() {
   String ^ pText = "Hello World! ";
   String ^ pCaption = "PInvoke Test";
   MessageBox(0, pText, pCaption, 0);
}
```

Výstupem je okno se zprávou, které má název PInvoke Test a obsahuje text Hello World!.

Informace zařazování se také používá u PInvoke k vyhledávání funkcí v knihovně DLL. V DLL knihovně user32.dll ve skutečnosti není funkce MessageBox ale CharSet = CharSet::Ansi, která umožňuje PInvoke použití ANSI verze funkce s názvem MessageBoxA místo Unicode verze funkce MessageBoxW. Obecně doporučujeme používat Unicode verze nespravovaného rozhraní API, protože to eliminuje režie na překlad z nativního Unicode formátu používaného u rozhraní .NET Framework na ANSI formát.

## <a name="when-not-to-use-pinvoke"></a>Kdy se nepoužívá PInvoke

PInvoke není vhodná pro všechny funkce jazyka C v knihovnách DLL. Předpokládejme, že je funkce MakeSpecial v DLL knihovně mylib.dll deklarována takto:

`char * MakeSpecial(char * pszString);`

Pokud používáme PInvoke v aplikaci Visual C++, pak doporučujeme psát následující:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

Zde je problémem to, že nemůžeme odstranit paměť pro nespravovaný řetězec vrácený funkcí MakeSpecial. Jiné funkce volané prostřednictvím PInvoke vrací ukazatel na vnitřní vyrovnávací paměť, která nemá být odebrána uživatelem. V tomto případe je použití funkce IJW jasnou volbou.

## <a name="limitations-of-pinvoke"></a>Omezení PInvoke

Nemůžete vracet stejný ukazatel, který je předáván nativní funkci jako parametr. Pokud nativní funkce vrátí ukazatel, který byl zařazen metodou PInvoke, může následovat poškození paměti a výjimky.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

Následující příklad ukazuje tento problém, kdy přesto, že se zdá být výstup programu správný, výstup přichází z uvolněné paměti.

```cpp
// platform_invocation_services_5.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
#include <limits.h>

ref struct MyPInvokeWrap {
public:
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]
   static String^ CharLower([In, Out] String ^);
};

int main() {
   String ^ strout = "AabCc";
   Console::WriteLine(strout);
   strout = MyPInvokeWrap::CharLower(strout);
   Console::WriteLine(strout);
}
```

## <a name="marshaling-arguments"></a>Argumenty zařazování

S `PInvoke` není nutné žádné zařazování mezi spravovanými a primitivními nativními typy jazyka C++ stejného formuláře. Například není požadováno žádné zařazování mezi Int32 a int nebo mezi Double a double.

Musíte však zařazovat typy, které nemají stejnou formu. Jedná se o typy char, string a struct. V následující tabulce jsou uvedena mapování používaná zařazováním pro různé typy:

|wtypes.h|Visual C++ –|Visual C++ s /clr|Common language runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|POPISOVAČ|anulovat \*|anulovat \*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|KRÁTKÝ|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|DLOUHÝ|long|long|Int32|
|LOGICK|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPCSTR|znak \*|Řetězec ^ [in], StringBuilder ^ [in, out]|Řetězec ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|\* const char|Řetězec ^|String|
|LPWSTR|wchar_t \*|Řetězec ^ [in], StringBuilder ^ [in, out]|Řetězec ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|const wchar_t \*|Řetězec ^|String|
|FLOAT|float|float|Jednoduché|
|DOUBLE|double|double|Double|

Zařazování automaticky připíná paměť přidělenou haldě modulu runtime, pokud je adresa předávána nespravované funkci. Připínání zabraňuje systému uvolňování paměti přesunout přidělený bloku paměti během komprimace.

V příkladu zmíněném výše v tomto tématu určuje parametr CharSet parametru DllImport, jak by měly být zařazeny spravované řetězce; v tomto případě by měl být zařazen do řetězce ANSI na nativní straně.

Můžete specifikovat zařazovací informace pro jednotlivé argumenty nativní funkce pomocí atributu MarshalAs. Existuje několik možností pro zařazování řetězce \* argument: BStr, ANSIBStr, TBStr, typem LPStr, LPWStr a LPTStr. Výchozí hodnota je LPStr.

V tomto příkladu je řetězec zařazen jako dvoubajtový Unicode řetězec znaků, LPWStr. Výstupem je první písmeno Hello World! vzhledem k tomu, že druhý bajt zařazeného řetězce má hodnotu null a přeloží tuto značku jako značku konce řetězce.

```cpp
// platform_invocation_services_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", EntryPoint="puts")]
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Atribut MarshalAs je v oboru názvů System::Runtime::InteropServices. Atribut lze použít s jinými datovými typy, jako jsou například pole (array).

Jak bylo zmíněno výše v tomto tématu, zařazovací knihovna poskytuje novou, optimalizovanou metodu zařazování dat mezi nativními a spravovanými prostředky. Další informace najdete v tématu [Přehled zařazování v C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Možné problémy s výkonem

PInvoke má režii mezi 10 a 30 x86 pokyny za volání. Vedle těchto pevně stanovených nákladů vytváří zařazování další režii. U přenositelných datových typů, které zabírají stejné množství spravovaného a nespravovaného kódu, nejsou žádné zařazovací náklady. Například převod mezi int a Int32 je bez nákladů.

Pro lepší výkon je vhodnější mít méně volání PInvoke, která zařazují největší možné množství údajů, než více volání, která zařazují pro každé volání méně údajů.

## <a name="see-also"></a>Viz také:

[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
