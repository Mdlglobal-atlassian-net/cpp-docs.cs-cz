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
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372514"
---
# <a name="calling-native-functions-from-managed-code"></a>Volání nativních funkcí ze spravovaného kódu

Běžný jazyk runtime poskytuje služby vyvolání platformy nebo PInvoke, který umožňuje spravovaný kód volat funkce stylu C v nativních dynamicky propojených knihoven (DLL). Stejné zařazování dat se používá jako pro interoperabilitu com s runtime a pro mechanismus "It Just Works" nebo IJW.

Další informace naleznete v tématu:

- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Ukázky v této části `PInvoke` jen ilustrují, jak lze použít. `PInvoke`můžete zjednodušit vlastní zařazování dat, protože poskytujete zařazování informace deklarativně v atributy namísto psaní procedurální zařazování kód.

> [!NOTE]
> Zařazovací knihovna poskytuje alternativní způsob, jak zařazovat data mezi nativní a spravovaná prostředí optimalizovaným způsobem. Další informace o zařazovací knihovně najdete [v tématu Přehled zařazování v jazyce C++.](../dotnet/overview-of-marshaling-in-cpp.md) Zařazování knihovny je použitelný pouze pro data a ne pro funkce.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke a atribut DllImport

Následující příklad ukazuje použití `PInvoke` v programu Visual C++. Nativní funkce umístí je definována v msvcrt.dll. DllImport atribut se používá pro deklaraci puts.

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

Následující vzorek je ekvivalentní předchozímu vzorku, ale používá IJW.

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

### <a name="advantages-of-ijw"></a>Výhody IJW

- Není nutné zapisovat `DLLImport` deklarace atributů pro nespravovaná úložiště API, která program používá. Stačí zahrnout soubor záhlaví a odkaz na knihovnu importu.

- Mechanismus IJW je o něco rychlejší (například zástupné procedury IJW nemusí kontrolovat potřebu připnout nebo kopírovat datové položky, protože to provádí explicitně vývojář).

- Jasně ilustruje problémy s výkonem. V tomto případě skutečnost, že překládáte z řetězce Unicode do řetězce ANSI a že máte přidělení paměti obsluhy a přidělení. V tomto případě vývojář psaní kódu pomocí IJW `_putws` by `PtrToStringChars` si uvědomit, že volání a použití by bylo lepší pro výkon.

- Pokud zavoláte mnoho nespravovaných api pomocí stejných dat, zařazování jednou a předávání zařazované kopie je mnohem efektivnější než re-zařazování pokaždé.

### <a name="disadvantages-of-ijw"></a>Nevýhody IJW

- Zařazování musí být zadáno explicitně v kódu namísto podle atributů (které mají často odpovídající výchozí hodnoty).

- Zařazovací kód je inline, kde je více invazivní v toku aplikační logiky.

- Vzhledem k tomu, `IntPtr` že explicitní zařazování api vrátit typy pro `ToPointer` 32bitové přenositelnosti 64 bitů, je nutné použít další volání.

Konkrétní metoda vystavená c++ je efektivnější, explicitní metoda, na úkor některé další složitosti.

Pokud aplikace používá hlavně nespravované datové typy nebo pokud volá více nespravovaných rozhraní API než rozhraní API rozhraní .NET Framework, doporučujeme použít funkci IJW. Chcete-li volat příležitostné nespravované rozhraní API v většinou spravované aplikace, volba je jemnější.

## <a name="pinvoke-with-windows-apis"></a>PInvoke s windows api

PInvoke je vhodný pro volání funkcí v systému Windows.

V tomto příkladu program Visual C++ spolupracuje s funkcí MessageBox, která je součástí rozhraní API Win32.

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

Výstup je okno se zprávou, které má název PInvoke Test a obsahuje text Hello World!.

Zařazování informace je také používán PInvoke vyhledat funkce v DLL. V user32.dll ve skutečnosti neexistuje žádná funkce MessageBox, ale CharSet=CharSet::Ansi umožňuje PInvoke používat MessageBoxA, ansi verzi, namísto MessageBoxW, což je verze Unicode. Obecně doporučujeme používat verze unicode nespravovaných rozhraní API, protože to eliminuje režii překladu z nativního formátu Unicode objektů řetězce rozhraní .NET Framework do ANSI.

## <a name="when-not-to-use-pinvoke"></a>Kdy nepoužívat PInvoke

Použití PInvoke není vhodné pro všechny funkce stylu C v knihovnách DLL. Předpokládejme například, že je funkce MakeSpecial v mylib.dll deklarována takto:

`char * MakeSpecial(char * pszString);`

Pokud používáme PInvoke v aplikaci Visual C++, můžeme napsat něco podobného následující:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

Problém je, že zde nelze odstranit paměť pro nespravovaný řetězec vrácený MakeSpecial. Další funkce volané prostřednictvím PInvoke vrátí ukazatel na vnitřní vyrovnávací paměť, která nemusí být vrácena uživatelem. V tomto případě je použití funkce IJW jasnou volbou.

## <a name="limitations-of-pinvoke"></a>Omezení Vyvolání

Nelze vrátit stejný přesný ukazatel z nativní funkce, kterou jste vzali jako parametr. Pokud nativní funkce vrátí ukazatel, který byl zařazen do něj PInvoke, může dojít k poškození paměti a výjimky.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

Následující ukázka vykazuje tento problém a přestože se může zdát, že program poskytuje správný výstup, výstup pochází z paměti, která byla uvolněna.

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

## <a name="marshaling-arguments"></a>Zařazovací argumenty

S `PInvoke`, žádné zařazování je potřeba mezi spravované a C++ nativní primitivní typy se stejným formulářem. Například žádné zařazování je vyžadováno mezi Int32 a int nebo mezi Double a double.

Je však nutné zařadit typy, které nemají stejný formulář. To zahrnuje char, řetězec a struct typy. V následující tabulce jsou uvedena mapování používaná zařazovacím úřadem pro různé typy:

|wtypes.h|Visual C++|Vizuální C++ s /clr|Běžný jazyk runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|Zpracování|Void\*|Void\*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|Krátké|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|Dlouhé|long|long|Int32|
|Bool|long|bool|Logická hodnota|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|Char|char|char|Char|
|LPSTR|Char\*|Řetězec ^ [in], StringBuilder ^ [in, out]|Řetězec ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char\*|Řetězec ^|Řetězec|
|LPWSTR|Wchar_t\*|Řetězec ^ [in], StringBuilder ^ [in, out]|Řetězec ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|wchar_t\*|Řetězec ^|Řetězec|
|Float|float|float|Single|
|Dvojité|double|double|Double|

Zařazování automaticky připne paměť přidělenou na haldě runtime, pokud je jeho adresa předána nespravované funkci. Připnutí zabrání uvolňování paměti přesunutí přiděleného bloku paměti během zhutnění.

V příkladu uvedeném výše v tomto tématu určuje parametr CharSet dllImport, jak by měly být zařazovány spravované řetězce; v tomto případě by měly být zařazeny do ansi řetězců pro nativní straně.

Informace o zařazování pro jednotlivé argumenty nativní funkce můžete zadat pomocí atributu MarshalAs. Existuje několik možností pro zařazování String \* argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr a LPTStr. Výchozí hodnota je LPStr.

V tomto příkladu je řetězec zařazen jako dvoubajtovský řetězec znaků Unicode LPWStr. Výstupem je první písmeno Hello World! protože druhý bajt zařazovaného řetězce je null a umístí interpretuje jako značku konce řetězce.

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

MarshalAs Atribut je v systémové::Runtime::InteropServices oboru názvů. Atribut lze použít s jinými datovými typy, jako jsou pole.

Jak již bylo zmíněno dříve v tématu, zařazovací knihovna poskytuje novou, optimalizovanou metodu zařazování dat mezi nativním a spravovaným prostředím. Další informace naleznete v [tématu Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Faktory ovlivňující výkon

PInvoke má režii mezi 10 a 30 x86 pokyny na volání. Kromě této pevné náklady zařazování vytvoří další režii. Neexistuje žádné náklady zařazování mezi přenositelné typy, které mají stejnou reprezentaci ve spravovaném a nespravovaném kódu. Například neexistuje žádné náklady na překlad mezi int a Int32.

Pro lepší výkon mají méně PInvoke volání, které zařazují co nejvíce dat, namísto více volání, které zařazují méně dat na volání.

## <a name="see-also"></a>Viz také

[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)
