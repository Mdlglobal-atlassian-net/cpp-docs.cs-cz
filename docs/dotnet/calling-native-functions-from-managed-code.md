---
title: Volání nativních funkcí ze spravovaného kódu | Microsoft Docs
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
ms.openlocfilehash: c0d7e69c95790122f44dc59d06f2843afbddfb2c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="calling-native-functions-from-managed-code"></a>Volání nativních funkcí ze spravovaného kódu
Modul common language runtime poskytuje služby volání nespravovaného nebo PInvoke, což umožňuje spravovat kód volat funkce jazyka C v nativní propojené dynamické knihovny (DLL). Stejné zařazování dat se používá jako Interoperabilita modelů COM s modulem runtime a pro "Prostě to funguje" nebo IJW, mechanismus.  
  
 Další informace naleznete v tématu:  
  
-   [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Vyvolání bližší pohled na platformy](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Ukázky v této části ukazují jak `PInvoke` lze použít. `PInvoke` můžete zjednodušit vlastní zařazování dat vzhledem k tomu, že zadáte zařazování informace deklarativně v atributech místo psaní procedurální zařazování kódu.  
  
> [!NOTE]
>  Knihovny zařazování poskytuje alternativní způsob zařazování dat mezi nativní a spravovaná prostředí optimálního. V tématu [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o knihovny zařazování. Je možné použít pouze data a ne pro funkce zařazování knihovnu.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke a atribut DllImport  
 Následující příklad ukazuje použití `PInvoke` v programu Visual C++. Nativní funkce vkládání je definována v msvcrt.dll. Atribut DllImport se používá pro deklaraci vkládání.  
  
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
  
 Následující příklad je ekvivalentní v předchozím příkladu, ale používá IJW.  
  
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
  
### <a name="advantages-of-ijw"></a>Výhody IJW  
  
-   Není nutné zapsat `DLLImport` atribut deklarace pro nespravovaná rozhraní API používá program. Zahrnout pouze záhlaví souboru a odkaz s knihovny importu.  
  
-   Mechanismus IJW je mírně rychlejší (například zástupných procedur IJW nemusí zjistit potřeba PIN kód nebo kopírování datových položek, protože je explicitně provádí vývojář).  
  
-   Jasně ukazuje problémy s výkonem. V takovém případě být skutečnost, že jsou překladu z řetězce Unicode do řetězce ANSI a přidělování paměti a navrácení. V takovém případě vývojář zapisování kódu pomocí IJW by potřeba si uvědomit, že volání `_putws` a pomocí `PtrToStringChars` by lepšího výkonu.  
  
-   Když zavoláte mnoho nespravovaná rozhraní API pomocí stejná data, jeho zařazování jednou a předávání zařazené kopie je mnohem efektivnější než znovu zařazování pokaždé, když.  
  
### <a name="disadvantages-of-ijw"></a>Nevýhody IJW  
  
-   Zařazování musí být určena explicitně v kódu místo atributy (které mají často vhodné výchozí nastavení).  
  
-   Kód zařazování je vložený, kde je v toku logiku aplikace.  
  
-   Protože explicitní zařazování rozhraní API vrací `IntPtr` typy pro 32bitové verze na 64-bit přenositelnost, je nutné použít velmi `ToPointer` volání.  
  
 Konkrétní metoda použitá v C++ je efektivnější, explicitní metoda, která potřebujete některé další složitosti.  
  
 Pokud aplikace používá převážně nespravované datové typy nebo pokud volá více nespravovaná rozhraní API než rozhraní API technologie .NET Framework, doporučujeme vám použít funkci IJW. Volba volat příležitostně nespravovaného rozhraní API ve většině případů spravované aplikaci, je další menší.  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke pomocí rozhraní API systému Windows  
 PInvoke je vhodné pro volání funkcí v systému Windows.  
  
 V tomto příkladu program Visual C++ spolupracuje s funkcí MessageBox, která je součástí rozhraní Win32 API.  
  
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
  
 Výstup se zprávou, která má název PInvoke Test a obsahuje text Hello, World!.  
  
 Zařazování informace slouží také pomocí služby PInvoke při vyhledávání funkcí v knihovně DLL. V user32.dll ve skutečnosti neexistuje žádná funkce MessageBox ale CharSet = CharSet::Ansi umožňuje PInvoke použití, verze ANSI místo funkce, což je verze kódování Unicode. Obecně doporučujeme používat kódování Unicode verze nespravovaného rozhraní API, protože eliminuje překlad režie z nativní formátu Unicode string objekty rozhraní .NET Framework na ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Kdy nepoužívat PInvoke  
 Pomocí služby PInvoke není vhodná pro všechny funkce jazyka C v knihovnách DLL. Předpokládejme například, že je funkce MakeSpecial v mylib deklarovaný následujícím způsobem:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Pokud používáme PInvoke v aplikaci Visual C++, vám doporučujeme psát podobný následujícímu:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 Zde je, že paměť pro nespravovaná řetězec vrácený MakeSpecial nelze odstranit. Další funkce volané prostřednictvím PInvoke vrací ukazatel na vnitřní vyrovnávací paměť, která nemusí být navrácena uživatelem. V takovém případě pomocí funkce IJW je zřejmé volbou.  
  
## <a name="limitations-of-pinvoke"></a>Omezení PInvoke  
 Stejný ukazatel nemůže vrátit z nativní funkce, který je předáván jako parametr. Pokud nativní funkce vrátí ukazatele, který byl zařazen do ní pomocí služby PInvoke, může následovat poškození paměti a výjimky.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 Následující příklad ukazuje problém, a to i v případě, že program zdá se, že správný, výstup pochází z paměti, který měl bylo uvolněno.  
  
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
  
## <a name="marshaling-arguments"></a>Zařazování argumenty  
 S `PInvoke`, není nutné žádné zařazování mezi spravovanými a C++ nativní primitivní typy stejného formuláře. Například žádné zařazování nebo se vyžaduje mezi Int32 a int, mezi Double a double.  
  
 Musí však zařazování typů, které nemají stejného formuláře. To zahrnuje typy char, string a struktura. V následující tabulce jsou uvedeny mapování používají zařazování pro různé typy:  
  
|wtypes.h|Visual C++|Visual C++ s volbou/CLR|Modul common language runtime|  
|--------------|------------------|-----------------------------|-----------------------------|  
|POPISOVAČ|void *|void *|IntPtr UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|KRÁTKÝ|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|CELÁ ČÍSLA|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|DLOUHÁ|long|long|Int32|  
|BOOL|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG –|unsigned long|unsigned long|UInt32|  
|CHAR –|char|char|Char|  
|LPCSTR|Char *|Řetězec ^ [v], StringBuilder ^ [v, out]|Řetězec ^ [v], StringBuilder ^ [v, out]|  
|LPCSTR|const char *|Řetězec ^|String|  
|LPWSTR|wchar_t *|Řetězec ^ [v], StringBuilder ^ [v, out]|Řetězec ^ [v], StringBuilder ^ [v, out]|  
|LPCWSTR|Const wchar_t *|Řetězec ^|String|  
|PLOVOUCÍ DESETINNÁ ČÁRKA|float|float|Single|  
|DOUBLE|double|double|Double|  
  
 Zařazování automaticky PIN kódy paměti přidělené v haldě modulu runtime, pokud jeho adresy je předán do nespravované funkce. Připnutí zabrání přesunutí přiděleného bloku paměti během komprimace uvolňování paměti.  
  
 V příkladu výše v tomto tématu, CharSet parametru DllImport Určuje, jak spravované řetězce by měl být zařazen; v takovém případě by měl být zařazen do řetězců ANSI pro nativní straně.  
  
 Zadávat lze zařazování informace pro jednotlivé argumenty nativní funkce pomocí MarshalAs atribut. Existuje několik možností pro zařazování řetězec * argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr a LPTStr. Výchozí hodnota je LPStr.  
  
 V tomto příkladu je řetězec zařazen jako řetězec znaků dvoubajtové znakové sady Unicode, LPWStr. Výstup je první písmeno Hello, World! protože druhý bajt zařazené řetězce, který má hodnotu null a vloží interpretuje jako značka ukončení řetězce.  
  
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
  
 Atribut MarshalAs je v prostoru System::Runtime:: oboru názvů. Atribut můžete použít s jinými typy dat, jako je například pole.  
  
 Jak je uvedeno výše v tomto tématu, knihovny zařazování poskytuje novou, optimalizovanou metodu zařazování dat mezi nativní a spravovaná prostředí. Další informace najdete v tématu [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Faktory ovlivňující výkon  
 PInvoke má režii 10 až 30 x86 pokyny za volání. Tuto pevnou náklady vytváří zařazování další režii. Neexistuje žádné zařazování náklady mezi přenositelné typy, které mají stejnou reprezentaci v spravovanými a nespravovanými kódu. Je třeba bez nákladů pro převod mezi int a Int32.  
  
 Pro lepší výkon máte méně volání PInvoke, které zařazování jako množství dat nejdříve místo další volání, které každé volání.  
  
## <a name="see-also"></a>Viz také  
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)