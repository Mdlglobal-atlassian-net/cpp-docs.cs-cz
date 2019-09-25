---
title: C++ – systém typů (moderní verze jazyka C++)
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: b947bd6955a80e051d1dab81061b4b2bf2ab19c8
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "69498632"
---
# <a name="c-type-system-modern-c"></a>C++ – systém typů (moderní verze jazyka C++)

Koncept *typu* je velmi důležitý v C++. Všechny proměnné, argumenty funkcí a návratové hodnoty funkcí musí mít typ, aby bylo možné je zkompilovat. Každému výrazu (včetně hodnot literálů) navíc kompilátor před vyhodnocením implicitně přidělí typ. Mezi příklady typů patří **int** pro ukládání integrálních hodnot, **Double** pro ukládání hodnot s plovoucí desetinnou čárkou (označované také jako *skalární* datové typy) nebo standardní knihovna tříd [std:: basic_string](../standard-library/basic-string-class.md) pro ukládání textu. Můžete vytvořit vlastní typ definováním **třídy** nebo **struktury**. Typ určuje velikost paměti, kterou chcete přidělit proměnné (nebo výsledku výrazu), druhy hodnot, které mohou být v dané proměnné uloženy, způsob interpretace těchto hodnot (jako vzorců bitů) a operace, které lze s proměnnou provést. Tento článek obsahuje přehled hlavních funkcí systému typů v jazyce C++.

## <a name="terminology"></a>Terminologie

**Proměnná**: Symbolický název množství dat, aby se název mohl použít pro přístup k datům, která odkazuje v celém rozsahu kódu, kde je definován. V C++ *proměnné je proměnná* obecně používána pro odkazování na instance skalárních datových typů, zatímco instance jiných typů se obvykle nazývají *objekty*.

**Objekt**: V zájmu jednoduchosti a konzistence používá tento článek termínový *objekt* pro odkazování na jakoukoli instanci třídy nebo struktury a při jejím použití v obecném smyslu zahrnuje všechny typy, dokonce i skalární proměnné.

**Typ pod** (prostá stará data): Tato neformální kategorie datových typů v C++ systému odkazuje na skalární typy (viz oddíl základní typy) nebo *třídy pod*. Třída POD nemá žádné statické datové členy, které nejsou rovněž POD, a nemá žádné uživatelem definované konstruktory, destruktory ani operátory přiřazení. Třída POD navíc nemá žádné virtuální funkce, žádnou základní třídu a žádné soukromé ani chráněné nestatické datové členy. Typy POD se často používají pro výměnu externích dat, například s modulem napsaným v jazyce C (který má pouze typy POD).

## <a name="specifying-variable-and-function-types"></a>Určení typů proměnných a funkcí

C++je jazyk *silného typu* a je také *staticky*typu; Každý objekt má typ a tento typ se nikdy nemění (nepleťte si se statickými datovými objekty).
**Pokud deklarujete proměnnou** v kódu, je nutné buď zadat typ explicitně, nebo použít klíčové slovo **auto** a instruovat kompilátor, aby odvodit typ z inicializátoru.
**Pokud deklarujete funkci** v kódu, je nutné zadat typ každého argumentu a jeho návratovou hodnotu nebo **Zrušit** , pokud funkce nevrátí žádnou hodnotu. Výjimkou je použití šablon funkce, které umožňují použití argumentů libovolných typů.

Po prvotním deklarování proměnné nelze její typ později změnit. Můžete však zkopírovat hodnotu proměnné nebo návratové hodnoty funkce do jiné proměnné jiného typu. Tyto operace se nazývají *převody typu*, které jsou někdy nezbytné, ale jsou také potenciálními zdroji ztráty dat nebo nesprávného fungování.

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

Na rozdíl od některých jazyků nemá C++ žádný univerzální základní typ, z něhož by byly odvozeny všechny ostatní typy. Jazyk obsahuje mnoho *základních typů*, označovaných také jako *předdefinované typy*. To zahrnuje číselné typy, jako je **int**, **Double**, **Long**, **bool**, a typy **char** a **wchar_t** pro znaky ASCII a Unicode, v uvedeném pořadí. Většina základních typů (s výjimkou **bool**, **Double**, **wchar_t** a souvisejících typů) mají všechny nepodepsané verze, které upravují rozsah hodnot, které může proměnná ukládat. Například **int**, který ukládá 32 celé číslo se znaménkem, může představovat hodnotu od-2 147 483 648 do 2 147 483 647. Celé **číslo bez znaménka**, které je také uloženo jako 32-bitů, může ukládat hodnotu od 0 do 4 294 967 295. Celkový počet možných hodnot je ve všech případech stejný, liší se pouze rozsah.

Základní typy jsou rozpoznávány kompilátorem, který má vestavěná pravidla určující, jaké operace lze s jednotlivými typy provádět a jak je lze převést na jiné základní typy. Úplný seznam předdefinovaných typů a jejich velikost a číselná omezení najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

Následující ilustrace znázorňuje relativní velikosti předdefinovaných typů:

![Velikost v bajtech z&#45;vestavěných typů](../cpp/media/built-intypesizes.png "velikosti v bajtech&#45;vestavěných typů")

V následující tabulce jsou uvedeny nejčastěji používané základní typy:

|Typ|Velikost|Komentář|
|----------|----------|-------------|
|int|4 bajty|Výchozí volba pro integrální hodnoty.|
|double|8 bajtů|Výchozí volba pro hodnoty s plovoucí desetinnou čárkou.|
|bool|1 bajt|Představuje hodnoty, které mohou být „true“ nebo „false“.|
|char|1 bajt|Používá se pro znaky standardu ASCII ve starších řetězcích stylu C nebo objektů std::string, které nikdy nebude nutné převést do kódování UNICODE.|
|wchar_t|2 bajty|Představuje hodnoty „širokých“ znaků, které mohou být kódovány ve formátu UNICODE (UTF-16 v systému Windows, v jiných operačních systémech se může lišit). Toto je typ znaku, který se používá v řetězcích typu `std::wstring`.|
|znak&nbsp;bez znaménka|1 bajt|C++nemá žádný předdefinovaný `byte` typ.  Umožňuje znázornit hodnotu bajtu pomocí unsigned char.|
|unsigned int|4 bajty|Výchozí volba pro bitové příznaky.|
|long long|8 bajtů|Představuje hodnoty tvořené vysokým celým číslem.|

## <a name="the-void-type"></a>Typ void

Typ **void** je speciální typ; nemůžete deklarovat proměnnou typu **void**, ale můžete deklarovat proměnnou typu __void \*__  (ukazatel na **void**), což je někdy nezbytné při přidělování nezpracované (netypové) paměti. Ukazatele na **typ void** však nejsou typově bezpečné a obecně se jejich použití v moderních C++případech nedoporučuje. V deklaraci funkce **void** návratová hodnota znamená, že funkce nevrací hodnotu. Toto je běžné a přijatelné použití **void**. I když jazyk C vyžaduje funkce, které mají nula parametrů pro deklaraci **void** v seznamu parametrů, například `fou(void)`, tento postup se nedoporučuje v moderních C++ a měl by být deklarovaný `fou()`. Další informace naleznete v tématu [převody typů a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Kvalifikátor typu const

Jakýkoli vestavěný nebo uživatelem definovaný typ může být kvalifikován pomocí klíčového slova const. Kromě toho členské funkce mohou být kvalifikovány jako **const**a dokonce i přetížení **const**. Hodnotu typu **const** nelze po inicializaci změnit.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.
```

Kvalifikátor **const** se v deklaracích funkcí a proměnných často používá a "konstanta const" je důležitým konceptem C++v nástroji; v podstatě znamená použití **const** k zaručení, v době kompilace, že hodnoty nejsou záměrně upravovány. Další informace naleznete v tématu [const](../cpp/const-cpp.md).

Typ **const** je odlišný od své nekonstantní verze; například **const int** je odlišný typ z **int**. V případě, že C++ je nutné odebrat *const-Ness* z proměnné, můžete použít operátor **const_cast** na těchto vzácných případech. Další informace naleznete v tématu [převody typů a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Typy řetězců

V jazyce není k C++ dispozici žádný vestavěný typ řetězce; **char** a **wchar_t** – jednotlivé znaky – je nutné deklarovat pole těchto typů pro aproximaci řetězce, přidáním ukončující hodnoty null (například ASCII `'\0'`) do prvku pole za posledním platným znakem (označuje se také jako *Řetězec ve stylu jazyka C*). Psaní řetězců ve stylu C vyžadovalo zapsat mnohem více kódu nebo využít funkce externí knihovny pro tvorbu řetězců. V moderních C++ale máme standardní typy `std::string` knihoven (pro 8bitové řetězce znaků typu **char**) nebo `std::wstring` (pro 16bitové řetězce znaků typu **wchar_t**). Tyto C++ knihovny standardních knihoven lze představit jako nativní řetězcové typy, protože jsou součástí standardních knihoven, které jsou zahrnuty v jakémkoli prostředí sestavení s C++ vyhovujícími verzemi. Stačí použít `#include <string>` direktivu k zpřístupnění těchto typů v programu. (Pokud používáte knihovnu MFC nebo ATL, je k dispozici také třída CString, ta ale není součástí standardu C++.) Použití polí znaků zakončených hodnotou null (výše zmíněné řetězce ve stylu C) se v moderním jazyce C++ důrazně nedoporučuje.

## <a name="user-defined-types"></a>Uživateli definované typy

Při definování **třídy**, **struktury**, **sjednocení**nebo **výčtu**je tato konstrukce použita ve zbytku kódu, jako by šlo o základní typ. Má známou velikost v paměti a na kontrolu doby kompilace a doby trvání programu při běhu se vztahují některá pravidla týkající se způsobu jeho použití. Nejdůležitější rozdíly mezi základními typy a typy definovanými uživateli jsou následující:

- Kompilátor neobsahuje žádné předdefinované informace o uživatelském typu. Učí se typu při prvním výskytu definice během procesu kompilace.

- Jako uživatel určujete, jaké operace lze s vaším typem provádět a jak ho lze převést na další typy. K tomu definujete (pomocí přetížení) příslušné operátory, buď jako členy třídy nebo jako nečlenské funkce. Další informace najdete v tématu [přetížení funkce](function-overloading.md) .

## <a name="pointer-types"></a>Typy ukazatelů

Dating zpět na nejstarší verze jazyka C a C++ nadále umožňuje deklarovat proměnnou typu ukazatele pomocí speciálního deklarátor `*` (hvězdička). Typ ukazatele ukládá adresu umístění v paměti, kde je uložena skutečná hodnota dat. V moderním C++se tyto odkazy označují jako *nezpracované ukazatele*a k nim ve vašem kódu přistupovaly prostřednictvím speciálních `*` operátorů (hvězdička) nebo `->` (pomlčka s větší-než). Tento postup se nazývá *přesměrování*a ten, který použijete, závisí na tom, zda provádíte přesměrování ukazatele na skalární nebo ukazatel na člen v objektu. Práce s typy ukazatelů byla dlouhou dobu jedním z nejsložitějších a nejvíce matoucích aspektů vývoje programů v jazycích C a C++. Tato část popisuje některé skutečnosti a postupy, které vám pomůžou při používání nezpracovaných ukazatelů, pokud chcete C++ , ale v moderních IT již není nutné (nebo se doporučuje) používat nezpracované ukazatele pro vlastnictví objektů na všech základě vývoje [inteligentního ukazatele](../cpp/smart-pointers-modern-cpp.md) (Další informace najdete v tématu. na konci této části). Nezpracované ukazatele lze stále s výhodou a bezpečně používat ke sledování objektů, pokud je však potřebujete použít pro vlastnictví objektu, měli byste tak činit s rozvahou a velmi pečlivě promyslet, jak se budou objekty vlastněné těmito ukazateli vytvářet a odstraňovat.

Základní princip, který byste měli znát, je, že deklarací proměnné nezpracovaného ukazatele se přidělí pouze paměť potřebná k uložení adresy umístění v paměti, na které bude ukazatel odkazovat při zrušení reference. Přidělení paměti pro samotnou hodnotu dat (označované také jako *záložní úložiště*) ještě není přiděleno. Jinými slovy, deklarováním proměnné nezpracovaného ukazatele vytváříte proměnnou adresy v paměti, nikoli skutečnou datovou proměnnou. Zrušení reference na proměnnou ukazatele, aniž byste se ujistili, že proměnná obsahuje platnou adresu záložního úložiště, způsobí v programu nedefinované chování (obvykle závažnou chybu). Následující příklad ukazuje tento druh chyby:

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

Příklad opraveného kódu používá místní paměť zásobníku k vytvoření záložního úložiště, `pNumber` které odkazuje na. Pro jednoduchost používáme základní typ. V praxi jsou záložní úložiště pro ukazatele často uživatelsky definovaných typů, které se dynamicky přidělují v oblasti paměti nazvané *halda* (nebo *bezplatné úložiště*) pomocí **nového** výrazu klíčového slova (v programování ve stylu C, starší .`malloc()` Použila se funkce běhové knihovny jazyka C). Po přidělení jsou tyto proměnné obvykle označovány jako objekty, zejména v případě, že jsou založeny na definici třídy. Paměť, která je přidělena **novému** , musí být odstraněna odpovídajícím příkazem **Delete** (nebo, pokud `malloc()` jste použili funkci k přidělení, běhové funkce `free()`jazyka C).

Je však snadné zapomenout odstranit dynamicky přidělený objekt – zejména v komplexním kódu, což způsobí, že chyba prostředku volala *nevracení paměti*. Z tohoto důvodu se používání nezpracovaných ukazatelů v moderním jazyce C++ nedoporučuje. Téměř vždy je lepší zabalit nezpracovaný ukazatel do [inteligentního ukazatele](../cpp/smart-pointers-modern-cpp.md), který automaticky uvolní paměť při vyvolání jeho destruktoru (když se kód z oboru inteligentního ukazatele překročí); Díky inteligentním ukazatelům prakticky eliminují celou třídu chyb v C++ programech. V následujícím příkladu předpokládejme `MyClass` , že je uživatelem definovaný typ, který má veřejnou metodu.`DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Další informace o inteligentních ukazatelích naleznete v tématu [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md).

Další informace o převodech ukazatelů naleznete v tématu [převody typů a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Další informace o ukazatelích obecně naleznete v tématu [ukazatelé](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Datové typy ve Windows

V klasickém programování Win32 pro jazyk C++C a většina funkcí používá makra definice typedef a #define specifická pro systém Windows ( `windef.h`definovaná v) k určení typů parametrů a vrácených hodnot. Tyto datové typy systému Windows jsou většinou pouze speciální názvy (aliasy) přidělenéC++ typům C/předdefinované typy. Úplný seznam těchto definice typedef a definic preprocesoru naleznete v tématu [Windows Data Types](/windows/win32/WinProg/windows-data-types). Některé tyto funkce typedef, jako např. HRESULT a LCID, jsou užitečné a mají popisný charakter. Jiné, například INT, nemají zvláštní význam a představují pouze aliasy základních typů jazyka C++. Další datové typy systému Windows si zachovaly názvy pocházející z dob programování v jazyce C a 16bitových procesorů a ve světě moderního hardwaru a operačních systémů již nemají místo ani smysl. K prostředí Windows Runtime knihovně jsou k dispozici také speciální datové typy, které jsou uvedeny jako [prostředí Windows Runtime Base Data Types](/windows/win32/WinRT/base-data-types). V moderním jazyce C++ platí obecná rada preferovat základní typy C++, pokud typ Windows nesděluje některý další význam o tom, jak má být daná hodnota interpretována.

## <a name="more-information"></a>Další informace

Další informace o systému typů v jazyce C++ naleznete v následujících tématech.

|||
|-|-|
|[Typy hodnot](../cpp/value-types-modern-cpp.md)|Popisuje *typy hodnot* spolu s problémy souvisejícími s jejich použitím.|
|[Převody typů a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Popisuje běžné problémy při převodu typů a ukazuje, jak se jim vyhnout.|

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět (moderní verze jazyka C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)
