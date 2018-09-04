---
title: Volání nativních funkcí ze spravovaného kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3ef47e3aeb8cfb18dd1eb6497c593d8cec26081b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678447"
---
# <a name="calling-native-functions-from-managed-code"></a>Volání nativních funkcí ze spravovaného kódu
Modul common language runtime poskytuje platformu vyvolání služby nebo PInvoke, což umožňuje spravovat kód volat funkce jazyka C v nativní propojenými dynamickými knihovnami (DLL). Stejné zařazování dat se používá také u interoperabilita modelů COM s modulem runtime a pro mechanismus "Prostě to funguje" nebo IJW.  
  
 Další informace naleznete v tématu:  
  
-   [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
 Příklady v tomto oddíle ukazují jak `PInvoke` lze použít. `PInvoke` můžete zjednodušit vlastní zařazování dat, protože poskytnete zařazovací informace deklarativně v atributech namísto v ručně psaném kódu.  
  
> [!NOTE]
>  Zařazovací knihovna poskytuje alternativní způsob zařazování dat mezi nativními a spravovanými prostředky optimalizované způsobem. Zobrazit [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o zařazovací knihovně. Knihovna zařazování je použitelná pouze pro data a ne pro funkce.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke a DllImport atribut  
 Následující příklad ukazuje použití `PInvoke` v programu v jazyce Visual C++. Nativní funkce vkládání je definována v souboru msvcrt.dll. Atribut DllImport se používá pro deklaraci vkládání.  
  
```  
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
  
 Následující příklad je ekvivalentní k předchozímu příkladu, ale rozdílem použití IJW.  
  
```  
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
  
-   Není nutné psát `DLLImport` atribut deklarace pro nespravovaná rozhraní API používá program. Obsahuje pouze hlavičku souboru a spojení s importovanou knihovnou.  
  
-   Mechanismus IJW je mírně rychlejší (například zástupné procedury IJW není nutné zjistit třeba PIN kód nebo kopírované datové položky, protože se explicitně provádí vývojář).  
  
-   Jasně ukazuje problémy s výkonem. V tomto případě fakt, že provádíte převod Unicode řetězce na řetězec ANSI a máte odebrání dodatečné paměti přidělování a navracení zpět. V takovém případě by vývojář kód s pomocí IJW Uvědomte si, že volání `_putws` a pomocí `PtrToStringChars` by bylo lepší pro výkon.  
  
-   Pokud voláte mnoho nespravovaných API rozhraní používajících stejná data, provedení jednoho zařazení a předání zařazené kopie je mnohem efektivnější než provádění zařazení vždy znovu.  
  
### <a name="disadvantages-of-ijw"></a>Nevýhody systému souborů IJW  
  
-   Zařazování musí být zadané explicitně v kódu namísto pomocí atributů (které mají často vhodné výchozí nastavení).  
  
-   Kód zařazování je vloženě, kde je v toku aplikační logiky invazivnější.  
  
-   Protože explicitní zařazování rozhraní API vrací `IntPtr` typy pro přenositelnost 32bitové na 64bitovou verzi, musíte použít další `ToPointer` volání.  
  
 Konkrétní metoda použitá v jazyce C++ je efektivnější, explicitní metoda, která za cenu některé další složitosti.  
  
 Pokud aplikace používá převážně nespravované datové typy nebo pokud volá více nespravované rozhraní API než rozhraní API .NET Framework, doporučujeme použití funkce IJW. Kontaktování občasné nespravované rozhraní API ve většině spravovaných aplikacích je složitější.  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke pomocí rozhraní Windows API  
 PInvoke je vhodné pro volání funkcí ve Windows.  
  
 V tomto příkladu spolupracuje program Visual C++ s funkcí MessageBox, která je součástí rozhraní API systému Win32.  
  
```  
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
  
 Výstupem je okno se zprávou, která má název PInvoke Test a obsahuje text Hello World!.  
  
 Zařazovací informace se také používá u PInvoke k vyhledávání funkcí v knihovně DLL. Na user32.dll není ve skutečnosti není funkce MessageBox ale CharSet = CharSet::Ansi umožňuje PInvoke použití ANSI verze namísto funkce, což je verze Unicode. Obecně doporučujeme používat Unicode verze nespravovaného rozhraní API, protože to eliminuje režie na překlad z nativního Unicode formátu řetězcových objektů rozhraní .NET Framework na ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Kdy se nepoužívá PInvoke  
 Pomocí služby PInvoke není vhodná pro všechny funkce jazyka C v knihovnách DLL. Předpokládejme například, že je funkce MakeSpecial v mylib.dll deklarována takto:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Pokud používáme PInvoke v aplikaci Visual C++, pak doporučujeme psát podobný následujícímu:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 Zde je, že nemůžeme odstranit paměť pro nespravovaný řetězec vrácený funkcí MakeSpecial. Jiné funkce volané prostřednictvím PInvoke vrací ukazatel na vnitřní vyrovnávací paměť, která nemá být odebrána uživatelem. V tomto případě použití funkce IJW je jasnou volbou.  
  
## <a name="limitations-of-pinvoke"></a>Omezení PInvoke  
 Nelze vrátit stejný ukazatel z nativní funkce, který je předáván jako parametr. Pokud nativní funkce vrátí ukazatel, který byl zařazen do ní metodou PInvoke, může následovat poškození paměti a výjimek.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 Následující příklad ukazuje tento problém, a i v případě, že program může jevit jako správný, výstup přichází z uvolněné paměti.  
  
```  
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
 S `PInvoke`, není nutné žádné zařazování mezi spravovanými a primitivními nativními C++ typy stejného formuláře. Například je žádné zařazování mezi Int32 a int nebo mezi Double a double.  
  
 Musíte však zařazovat typy, které nemají stejnou formu. Jedná se o typy char, string a struct. V následující tabulce jsou uvedeny mapování používaná zařazováním pro různé typy:  
  
|wtypes.h|Visual C++|Visual C++ s parametrem/CLR|Modul common language runtime|  
|--------------|------------------|-----------------------------|-----------------------------|  
|POPISOVAČ|Typ void \*|Typ void \*|IntPtr UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|KRÁTKÉ|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|LONG|long|long|Int32|  
|BOOL|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|Char \*|Řetězec ^ [in], StringBuilder ^ [v, out]|Řetězec ^ [in], StringBuilder ^ [v, out]|  
|LPCSTR|const char \*|Řetězec ^|String|  
|LPWSTR|wchar_t \*|Řetězec ^ [in], StringBuilder ^ [v, out]|Řetězec ^ [in], StringBuilder ^ [v, out]|  
|LPCWSTR|Const wchar_t \*|Řetězec ^|String|  
|PLOVOUCÍ DESETINNOU ČÁRKOU|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 Zařazování automaticky připíná paměť přidělenou haldě modulu runtime, pokud je adresa předávána nespravované funkci. Připínání zabraňuje systému uvolňování paměti přesunout přidělený bloku paměti během komprimace.  
  
 V příkladu zmíněném výše v tomto tématu určuje parametr CharSet parametru DllImport, jak spravované řetězce by měly být zařazeny; v takovém případě by měl být zařazen do řetězce ANSI na nativní straně.  
  
 Můžete zadat zařazovací informace pro jednotlivé argumenty nativní funkce pomocí atributu MarshalAs. Existuje několik možností pro zařazování řetězce \* argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr a LPTStr. Výchozí hodnota je LPStr.  
  
 V tomto příkladu je řetězec zařazen jako dvoubajtový řetězec znaků Unicode, LPWStr. Výstupem je první písmeno Hello World! protože druhý bajt zařazeného řetězce je null a vloží interprety jako značku ukončení řetězce.  
  
```  
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
  
 Atribut MarshalAs je v oboru názvů System::Runtime:: InteropServices. Atribut lze použít s jinými datovými typy, jako je například pole.  
  
 Jak je uvedeno výše v tomto tématu, zařazovací knihovna poskytuje novou, optimalizovanou metodu zařazování dat mezi nativními a spravovanými prostředími. Další informace najdete v tématu [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Faktory ovlivňující výkon  
 PInvoke má režii mezi 10 a 30 x86 pokyny za volání. Vedle těchto pevně stanovených nákladů vytváří zařazování další režii. U přenositelných datových typů, které zabírají stejné množství spravovaného a nespravovaného kódu není žádné zařazovací náklady. Například je zdarma pro převod mezi int a Int32.  
  
 Pro zajištění lepšího výkonu máte méně volání PInvoke, která zařazují pro množství dat nejdříve, než více volání, která zařazují pro každé volání méně údajů.  
  
## <a name="see-also"></a>Viz také  
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)