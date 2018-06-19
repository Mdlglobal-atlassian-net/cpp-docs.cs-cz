---
title: C++ – systém typů (moderní verze jazyka C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c017b7048c8b62f58068d22b8efefd72f31d4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418507"
---
# <a name="c-type-system-modern-c"></a>C++ – systém typů (moderní verze jazyka C++)
Koncept *typu* je velmi důležité v jazyce C++. Všechny proměnné, argumenty funkcí a návratové hodnoty funkcí musí mít typ, aby bylo možné je zkompilovat. Každému výrazu (včetně hodnot literálů) navíc kompilátor před vyhodnocením implicitně přidělí typ. Některé příklady typů `int` k uložení celočíselné hodnoty, `double` pro uložení hodnot s plovoucí desetinnou čárkou (také označované jako *skalární* datových typů), nebo třída standardní knihovna [std::basic_string](../standard-library/basic-string-class.md) k ukládání textu. Můžete vytvořit vlastní typ definováním `class` nebo `struct`. Typ určuje velikost paměti, kterou chcete přidělit proměnné (nebo výsledku výrazu), druhy hodnot, které mohou být v dané proměnné uloženy, způsob interpretace těchto hodnot (jako vzorců bitů) a operace, které lze s proměnnou provést. Tento článek obsahuje přehled hlavních funkcí systému typů v jazyce C++.  
  
## <a name="terminology"></a>Terminologie  
 **Proměnné**: symbolický odkaz název množství dat, aby název můžete použít pro přístup k datům odkazuje v rámci rozsahu kódu, kde je definován. V jazyce C++ *proměnná* obecně slouží k odkazování na instancí skalární datových typů, zatímco se obvykle označují jako instancí jiné typy *objekty*.  
  
 **Objekt**: kvůli jednoduchosti a přehlednosti, tento článek používá termín *objekt* odkazovat na jakoukoli instanci třídu nebo strukturu, a pokud se používá v tom smyslu, Obecné obsahuje všechny typy, dokonce i skalární proměnné.  
  
 **Typ POD** (prostý stará data): tuto kategorii neformální datových typů v jazyce C++ odkazuje na typy, které jsou skalární (naleznete v části základní typy) nebo *POD třídy*. Třída POD nemá žádné statické datové členy, které nejsou rovněž POD, a nemá žádné uživatelem definované konstruktory, destruktory ani operátory přiřazení. Třída POD navíc nemá žádné virtuální funkce, žádnou základní třídu a žádné soukromé ani chráněné nestatické datové členy. Typy POD se často používají pro výměnu externích dat, například s modulem napsaným v jazyce C (který má pouze typy POD).  
  
## <a name="specifying-variable-and-function-types"></a>Určení typů proměnných a funkcí  
 Je C++ *silného typu* jazyk a je také *staticky typované*; každý objekt má typ a který typ nikdy změny (není Nezaměňovat s objekty statických dat).   
**Když je deklarovat proměnnou** ve vašem kódu, musíte buď explicitně zadat typ nebo použijte `auto` – klíčové slovo kompilátoru odvodit typ z inicializátoru.   
**Když je funkce deklarovat** v kódu, je nutné zadat typ každý argument a hodnoty, nebo `void` Pokud žádná hodnota je vráceným funkcí. Výjimkou je použití šablon funkce, které umožňují použití argumentů libovolných typů.  
  
 Po prvotním deklarování proměnné nelze její typ později změnit. Můžete však zkopírovat hodnotu proměnné nebo návratové hodnoty funkce do jiné proměnné jiného typu. Tyto operace se nazývají *převody typu*, které jsou někdy nezbytné, ale jsou také zdroje potenciální ztrátě dat nebo nesprávnosti.  
  
 Po deklarování proměnné typu POD důrazně doporučujeme ji inicializovat, což znamená, že jí přiřadíte počáteční hodnotu. Dokud proměnnou neinicializujete, má hodnotu „garbage“, která se skládá z jakýchkoli bitů, které se původně nacházely v daném umístění v paměti. To je důležitý aspekt jazyka C++. Nezapomeňte na něj zejména v případě, že přecházíte z jiného jazyka, který zpracovává inicializaci za vás. Při deklarování proměnné jiného typu třídy než POD zpracovává inicializaci konstruktor.  
  
 Následující příklad ukazuje některé jednoduché deklarace proměnných s popisem každé z nich. Příklad také ukazuje, jak kompilátor používá informace o typu k tomu, aby povolil nebo zakázal určité následné operace s proměnnou.  
  
```cpp  
  
int result = 0;              // Declare and initialize an integer.  
double coefficient = 10.8;   // Declare and initialize a floating   
                             // point value.  
auto name = "Lady G.";       // Declare a variable and let compiler   
                             // deduce the type.  
auto address;                // error. Compiler cannot deduce a type   
                             // without an intializing value.  
age = 12;                    // error. Variable declaration must  
                             // specify a type or use auto!  
result = "Kenny G.";         // error. Can’t assign text to an int.  
string result = "zero";      // error. Can’t redefine a variable with  
                             // new type.  
int maxValue;                // Not recommended! maxValue contains   
                             // garbage bits until it is initialized.  
  
```  
  
## <a name="fundamental-built-in-types"></a>Základní (vestavěné) typy  
 Na rozdíl od některých jazyků nemá C++ žádný univerzální základní typ, z něhož by byly odvozeny všechny ostatní typy. Provádění jazyka Visual C++ zahrnuje mnoho *základní typy*, také známé jako *vestavěné typy*. To zahrnuje číselnými typy, jako `int`, `double`, `long`, `bool`, a `char` a `wchar_t` typy pro znaky ASCII a UNICODE, v uvedeném pořadí. Většina základních typů (s výjimkou `bool`, `double`, `wchar_t` a související typy) všechny mít nepodepsané verze, které upravit rozsah hodnot, které můžou ukládat proměnnou. Například `int`, která ukládá 32-bit znaménkem, může představovat hodnotu z-2,147,483,648 na 2 147 483 647. `unsigned int`, Což je také uloženo jako 32 bity můžete ukládat hodnotu od 0 do 4 294 967 295. Celkový počet možných hodnot je ve všech případech stejný, liší se pouze rozsah.  
  
 Základní typy jsou rozpoznávány kompilátorem, který má vestavěná pravidla určující, jaké operace lze s jednotlivými typy provádět a jak je lze převést na jiné základní typy. Úplný seznam předdefinovaných typů a jejich velikost a číselné omezení, najdete v části [základní typy](../cpp/fundamental-types-cpp.md).  
  
 Následující ilustrace znázorňuje relativní velikosti předdefinovaných typů:  
  
 ![Velikost v bajtech vytvořené&#45;v typech](../cpp/media/built-intypesizes.png "předdefinované inTYpeSizes")  
  
 V následující tabulce jsou uvedeny nejčastěji používané základní typy:  
  
|Typ|Velikost|Komentář|  
|----------|----------|-------------|  
|int|4 bajty|Výchozí volba pro integrální hodnoty.|  
|double|8 bajtů|Výchozí volba pro hodnoty s plovoucí desetinnou čárkou.|  
|bool|1 bajt|Představuje hodnoty, které mohou být „true“ nebo „false“.|  
|char|1 bajt|Používá se pro znaky standardu ASCII ve starších řetězcích stylu C nebo objektů std::string, které nikdy nebude nutné převést do kódování UNICODE.|  
|wchar_t|2 bajtů|Představuje hodnoty „širokých“ znaků, které mohou být kódovány ve formátu UNICODE (UTF-16 v systému Windows, v jiných operačních systémech se může lišit). Jedná se o typ znak, který se používá v řetězcích typu `std::wstring`.|  
|unsigned char|1 bajt|C++ nemá žádnou integrovanou `byte` typu.  Umožňuje znázornit hodnotu bajtu pomocí unsigned char.|  
|unsigned int|4 bajty|Výchozí volba pro bitové příznaky.|  
|long long|8 bajtů|Představuje hodnoty tvořené vysokým celým číslem.|  
  
## <a name="the-void-type"></a>Typ void  
 `void` Typu, je zvláštním typem; nelze deklarovat proměnnou typu `void`, ale můžou deklarovat proměnnou typu `void *` (ukazatel na `void`), který je někdy nezbytné při přidělování paměti nezpracovaná (beztypové). Ale ukazatele na `void` jsou není bezpečný a obecně pro jejich používání není doporučeno v moderní verze jazyka C++. V deklaraci funkce `void` návratová hodnota znamená, že funkce nevrátí hodnotu; to je běžné a přijatelné používání z `void`. Při jazyk požadované funkce C, které mají žádné parametry deklarovat `void` v seznamu parametrů, například `fou(void)`, tento postup se nedoporučuje v moderní verze jazyka C++ a musí být deklarován `fou()`. Další informace najdete v tématu [typ převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
## <a name="const-type-qualifier"></a>Kvalifikátor typu const  
 Jakýkoli vestavěný nebo uživatelem definovaný typ může být kvalifikován pomocí klíčového slova const. Kromě toho může být členské funkce `const`-kvalifikovaný a to i v `const`-přetížený. Hodnota `const` typ nelze změnit, jakmile je inicializován.  
  
```cpp  
  
const double PI = 3.1415;  
PI = .75 //Error. Cannot modify const variable.  
  
```  
  
 `const` Kvalifikátor je často používány v deklaracích funkce a proměnné a "const správnost" Důležitou koncepcí v jazyce C++, v podstatě znamená používání `const` zaručit při kompilaci, že nejsou neúmyslně měnit hodnoty . Další informace najdete v tématu [const](../cpp/const-cpp.md).  
  
 A `const` typu se liší od jeho verze není const; například `const int` je typu distinct z `int`. Můžete použít C++ `const_cast` operátor na těchto výjimečných případech, kdy je nutné odebrat *const obchodní* z proměnné. Další informace najdete v tématu [typ převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
## <a name="string-types"></a>Typy řetězců  
 Přesněji řečeno jazyk C++ nemá žádný typ předdefinované řetězec; `char` a `wchar_t` ukládání jedné znaků – je potřeba deklarovat pole z těchto typů sblížit řetězec, přidání ukončující hodnotu null (například ASCII `'\0'`) na jeden element pole za poslední neplatný znak (také nazývané *C-style řetězec*). Psaní řetězců ve stylu C vyžadovalo zapsat mnohem více kódu nebo využít funkce externí knihovny pro tvorbu řetězců. Ale v moderní verze jazyka C++, typy standardní knihovny `std::string` (pro 8bitové `char`– typ řetězce znaků) nebo `std::wstring` (pro 16bitové `wchar_t`– typ řetězce znaků). Tyto kontejnery standardní knihovna C++ můžete představit jako typy nativní řetězce vzhledem k tomu, že jsou součástí standardní knihovny, které jsou součástí žádné kompatibilní sestavení prostředí C++. Jednoduše použijte `#include <string>` – direktiva, aby se tyto typy k dispozici v programu. (Pokud používáte knihovnu MFC nebo ATL, je k dispozici také třída CString, ta ale není součástí standardu C++.) Použití polí znaků zakončených hodnotou null (výše zmíněné řetězce ve stylu C) se v moderním jazyce C++ důrazně nedoporučuje.  
  
## <a name="user-defined-types"></a>Uživateli definované typy  
 Když definujete `class`, `struct`, `union`, nebo `enum`, že konstrukce se používá ve zbývající části kódu, jako by šlo základní typ. Má známou velikost v paměti a na kontrolu doby kompilace a doby trvání programu při běhu se vztahují některá pravidla týkající se způsobu jeho použití. Nejdůležitější rozdíly mezi základními typy a typy definovanými uživateli jsou následující:  
  
-   Kompilátor neobsahuje žádné předdefinované informace o uživatelském typu. Ho zjišťuje typu, když narazí definici během kompilace.  
  
-   Jako uživatel určujete, jaké operace lze s vaším typem provádět a jak ho lze převést na další typy. K tomu definujete (pomocí přetížení) příslušné operátory, buď jako členy třídy nebo jako nečlenské funkce. Další informace najdete v tématu [přetížení funkcí](function-overloading.md).  
  
-   Není nutné zadávat typy staticky (pravidlo, že typ objektu se nikdy nemění). Prostřednictvím mechanismy na *dědičnosti* a *polymorfismus*, proměnná deklarován jako typ uživatelem definované třídy (označované jako instanci objektu třídy) může mít jiný typ při spuštění než v Doba kompilace. Další informace najdete v tématu [dědičnosti](../cpp/inheritance-cpp.md).  
  
## <a name="pointer-types"></a>Typy ukazatelů  
 Z roku nejstarší verze jazyka C, C++ nadále umožňují deklarace proměnné typu ukazatele pomocí speciální deklarátor `*` (hvězdičky *). Typ ukazatele ukládá adresu umístění v paměti, kde je uložena skutečná hodnota dat. V moderní verze jazyka C++, to se označuje jako *nezpracovaná ukazatele*a ke kterým se přistupuje ve vašem kódu prostřednictvím speciální operátory `*` (hvězdičky *) nebo `->` (čárka s větší – než). To se označuje jako *vyhodnocení*, a které ten, který použijete, závisí na tom, jestli jsou vyhodnocení ukazatel na skalární hodnota nebo ukazatel na člena v objektu. Práce s typy ukazatelů byla dlouhou dobu jedním z nejsložitějších a nejvíce matoucích aspektů vývoje programů v jazycích C a C++. Tato část popisuje některé faktů a postupy pro zlepšení použijte nezpracovaná ukazatele, pokud chcete, ale v moderní verze jazyka C++ už obsahuje požadované (nebo doporučené) používat nezpracovaná ukazatele pro přenos vlastnictví objektu vůbec, z důvodu vývoj [chytré ukazatele](../cpp/smart-pointers-modern-cpp.md) () uvedeny další na konci této části). Nezpracované ukazatele lze stále s výhodou a bezpečně používat ke sledování objektů, pokud je však potřebujete použít pro vlastnictví objektu, měli byste tak činit s rozvahou a velmi pečlivě promyslet, jak se budou objekty vlastněné těmito ukazateli vytvářet a odstraňovat.  
  
 Základní princip, který byste měli znát, je, že deklarací proměnné nezpracovaného ukazatele se přidělí pouze paměť potřebná k uložení adresy umístění v paměti, na které bude ukazatel odkazovat při zrušení reference. Přidělení paměti pro vlastní hodnota dat (také nazývané *záložnímu úložišti*) ještě není přidělena. Jinými slovy, deklarováním proměnné nezpracovaného ukazatele vytváříte proměnnou adresy v paměti, nikoli skutečnou datovou proměnnou. Zrušení reference na proměnnou ukazatele, aniž byste se ujistili, že proměnná obsahuje platnou adresu záložního úložiště, způsobí v programu nedefinované chování (obvykle závažnou chybu). Následující příklad ukazuje tento druh chyby:  
  
```cpp  
  
int* pNumber;       // Declare a pointer-to-int variable.  
*pNumber = 10;      // error. Although this may compile, it is  
                    // a serious error. We are dereferencing an  
                    // uninitialized pointer variable with no  
                    // allocated memory to point to.  
  
```  
  
 V příkladu dochází ke zrušení reference na typ ukazatele bez přidělení paměti, kde by byla uložena skutečná celočíselná data, a bez přidělení platné adresy v paměti. Následující kód tyto chyby opravuje:  
  
```cpp  
  
    int number = 10;          // Declare and initialize a local integer  
                              // variable for data backing store.  
    int* pNumber = &number;   // Declare and initialize a local integer  
                              // pointer variable to a valid memory  
                              // address to that backing store.  
...  
    *pNumber = 41;            // Dereference and store a new value in   
                              // the memory pointed to by  
                              // pNumber, the integer variable called  
                              // "number". Note "number" was changed, not  
                              // "pNumber".  
  
```  
  
 Opravené kód příklad používá místní zásobníku paměti k vytvoření základní úložiště, který `pNumber` odkazuje na. Pro jednoduchost používáme základní typ. V praxi, úložiště zálohování pro ukazatele se většina často uživatelem definované typy, které jsou dynamicky přidělené v oblast paměti volat *haldy* (nebo *volné úložiště*) pomocí `new` – klíčové slovo výraz (ve stylu jazyka C programování starší `malloc()` použila funkce knihoven C runtime). Jakmile přiděleno, tyto proměnné se obvykle označují jako objekty, zejména v případě, že jsou založené na definici třídy. Paměť, která je přidělena s `new` musí být odstraněn odpovídající `delete` – příkaz (nebo, pokud jste použili `malloc()` funkce přidělit ji funkci C runtime `free()`).  
  
 Je však snadno zapomněli odstranit dynamicky přidělené objekt-zejména v složitý kód, což způsobí, že chyby prostředků názvem *nevrácená paměť systému*. Z tohoto důvodu se používání nezpracovaných ukazatelů v moderním jazyce C++ nedoporučuje. Je téměř vždy lepší zabalit nezpracovaná ukazatel v [chytré ukazatele](../cpp/smart-pointers-modern-cpp.md), který automaticky vydá paměť při vyvolání jeho – destruktor (Pokud je kód ocitne mimo rozsah pro inteligentní ukazatele); pomocí chytré ukazatele je prakticky Odstraňte celou třídu chyby v C++ programy. V následujícím příkladu se předpokládá `MyClass` je uživatelem definovaný typ, který má veřejná metoda `DoSomeWork();`  
  
```cpp  
  
void someFunction() {  
    unique_ptr<MyClass> pMc(new MyClass);  
    pMc->DoSomeWork();  
}  
  // No memory leak. Out-of-scope automatically calls the destructor  
  // for the unique_ptr, freeing the resource.  
  
```  
  
 Chytré ukazatele na další informace najdete v tématu [chytré ukazatele](../cpp/smart-pointers-modern-cpp.md).  
  
 Převody ukazatele na další informace najdete v tématu [typ převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
 Další informace o ukazatele obecně platí, najdete v části [ukazatele](../cpp/pointers-cpp.md).  
  
## <a name="windows-data-types"></a>Datové typy ve Windows  
 V classic Win32 programování pro C a C++, většina funkcí pomocí definice TypeDef specifické pro systém Windows a #define makra (definované v `windef.h`) určit typy parametry a návratové hodnoty. Tyto datové typy systému Windows jsou většinou právě speciální názvy (aliasy) na předdefinované typy jazyka C/C++. Úplný seznam těchto – definice TypeDef a definice preprocesoru najdete v tématu [Windows datové typy](http://msdn.microsoft.com/en-us/4553cafc-450e-4493-a4d4-cb6e2f274d46). Některé tyto funkce typedef, jako např. HRESULT a LCID, jsou užitečné a mají popisný charakter. Jiné, například INT, nemají zvláštní význam a představují pouze aliasy základních typů jazyka C++. Další datové typy systému Windows si zachovaly názvy pocházející z dob programování v jazyce C a 16bitových procesorů a ve světě moderního hardwaru a operačních systémů již nemají místo ani smysl. Existují také speciální datové typy, které jsou přidružené ke knihovně Windows Runtime, uveden jako [prostředí Windows Runtime základní datové typy](http://msdn.microsoft.com/en-us/b5735851-ec07-48c1-92b4-ca9f768096f6). V moderním jazyce C++ platí obecná rada preferovat základní typy C++, pokud typ Windows nesděluje některý další význam o tom, jak má být daná hodnota interpretována.  
  
## <a name="more-information"></a>Další informace  
 Další informace o systému typů v jazyce C++ naleznete v následujících tématech.  
  
|||  
|-|-|  
|[Typy hodnot](../cpp/value-types-modern-cpp.md)|Popisuje *typů hodnot* spolu se problémy týkající se jejich použití.|  
|[Typ převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Popisuje běžné problémy při převodu typů a ukazuje, jak se jim vyhnout.|  
  
## <a name="see-also"></a>Viz také  
 [C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)   
 [Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
