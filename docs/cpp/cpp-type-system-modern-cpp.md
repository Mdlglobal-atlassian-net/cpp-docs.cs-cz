---
title: C++ – systém typů (moderní verze jazyka C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
ms.openlocfilehash: 3e500980fbb5e6397e992f53b58f28fa710e7af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602602"
---
# <a name="c-type-system-modern-c"></a>C++ – systém typů (moderní verze jazyka C++)

Koncept *typ* je v jazyce C++ velmi důležitý. Všechny proměnné, argumenty funkcí a návratové hodnoty funkcí musí mít typ, aby bylo možné je zkompilovat. Každému výrazu (včetně hodnot literálů) navíc kompilátor před vyhodnocením implicitně přidělí typ. Mezi typy patří **int** pro ukládání integrálních hodnot, **double** k ukládání hodnot s plovoucí desetinnou čárkou (označované také jako *skalární* datové typy), nebo standardní knihovna tříd [std::basic_string](../standard-library/basic-string-class.md) pro ukládání textu. Můžete vytvořit vlastní typ definováním **třídy** nebo **struktura**. Typ určuje velikost paměti, kterou chcete přidělit proměnné (nebo výsledku výrazu), druhy hodnot, které mohou být v dané proměnné uloženy, způsob interpretace těchto hodnot (jako vzorců bitů) a operace, které lze s proměnnou provést. Tento článek obsahuje přehled hlavních funkcí systému typů v jazyce C++.

## <a name="terminology"></a>Terminologie

**Proměnné**: symbolický název množství dat tak, aby název lze použít pro přístup k datům, na který odkazuje v rámci rozsahu kódu, kde je definován. V jazyce C++ *proměnnou* se obecně používá k označování instancí skalárních datových typů, že instance ostatních typů se obvykle nazývají *objekty*.

**Objekt**: kvůli jednoduchosti a přehlednosti, tento článek používá termín *objekt* k odkazování na jakoukoli instanci třídy nebo struktury a používá se v obecném smyslu tento pojem zahrnuje všechny typy, včetně skalárních proměnných.

**Typ POD** (obyčejná stará data): Tato neformální kategorie datových typů jazyka C++ odkazuje na Skalární typy (viz oddíl základní typy) nebo jsou *třídy POD*. Třída POD nemá žádné statické datové členy, které nejsou rovněž POD, a nemá žádné uživatelem definované konstruktory, destruktory ani operátory přiřazení. Třída POD navíc nemá žádné virtuální funkce, žádnou základní třídu a žádné soukromé ani chráněné nestatické datové členy. Typy POD se často používají pro výměnu externích dat, například s modulem napsaným v jazyce C (který má pouze typy POD).

## <a name="specifying-variable-and-function-types"></a>Určení typů proměnných a funkcí

C++ je *silného typu* jazyk a je také *staticky typovaný*; každý objekt má typ, který se nikdy nemění (Nepleťte si se statickými datovými objekty).
**Pokud deklarujete proměnnou** ve vašem kódu, musíte buď explicitně zadat její typ nebo použít **automaticky** – klíčové slovo, abyste instruovali kompilátor k odvození typu z inicializátoru.
**Pokud deklarujete funkci** ve vašem kódu, je třeba zadat typ každého argumentu a vrácenou hodnota, nebo **void** Pokud funkcí není vrácena žádná hodnota. Výjimkou je použití šablon funkce, které umožňují použití argumentů libovolných typů.

Po prvotním deklarování proměnné nelze její typ později změnit. Můžete však zkopírovat hodnotu proměnné nebo návratové hodnoty funkce do jiné proměnné jiného typu. Tyto operace jsou označovány jako *převody typů*, které jsou někdy nezbytné, ale představují potenciální riziko ztráty dat nebo nepřesnosti.

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

Na rozdíl od některých jazyků nemá C++ žádný univerzální základní typ, z něhož by byly odvozeny všechny ostatní typy. Implementace jazyka Visual C++ obsahuje mnoho *základní typy*, označované také jako *předdefinovaných typů*. To zahrnuje číselné typy jako **int**, **double**, **dlouhé**, **bool**, plus **char** a **wchar_t** typy pro znaky ASCII a UNICODE v uvedeném pořadí. Většina základních typů (s výjimkou **bool**, **double**, **wchar_t** a souvisejících typů) mají všechny nepodepsané verze, které upravují rozsah hodnot, které může proměnná ukládat. Například **int**, který ukládá 32bitové celé číslo se znaménkem, může představovat hodnotu od-2,147,483,648 do 2 147 483 647. **Unsigned int**, která je také uložena jako 32bitová, může ukládat hodnotu od 0 do 4 294 967 295. Celkový počet možných hodnot je ve všech případech stejný, liší se pouze rozsah.

Základní typy jsou rozpoznávány kompilátorem, který má vestavěná pravidla určující, jaké operace lze s jednotlivými typy provádět a jak je lze převést na jiné základní typy. Úplný seznam předdefinovaných typů a jejich velikosti a číselné limitů naleznete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

Následující ilustrace znázorňuje relativní velikosti předdefinovaných typů:

![Velikost v bajtech vytvořené&#45;v typech](../cpp/media/built-intypesizes.png "předdefinované inTYpeSizes")

V následující tabulce jsou uvedeny nejčastěji používané základní typy:

|Typ|Velikost|Komentář|
|----------|----------|-------------|
|int|4 bajty|Výchozí volba pro integrální hodnoty.|
|double|8 bajtů|Výchozí volba pro hodnoty s plovoucí desetinnou čárkou.|
|bool|1 bajt|Představuje hodnoty, které mohou být „true“ nebo „false“.|
|char|1 bajt|Používá se pro znaky standardu ASCII ve starších řetězcích stylu C nebo objektů std::string, které nikdy nebude nutné převést do kódování UNICODE.|
|wchar_t|2 bajty|Představuje hodnoty „širokých“ znaků, které mohou být kódovány ve formátu UNICODE (UTF-16 v systému Windows, v jiných operačních systémech se může lišit). Toto je typ znaku, který se používá v řetězcích typu `std::wstring`.|
|unsigned char|1 bajt|Jazyk C++ nemá žádný předdefinovaný `byte` typu.  Umožňuje znázornit hodnotu bajtu pomocí unsigned char.|
|unsigned int|4 bajty|Výchozí volba pro bitové příznaky.|
|long long|8 bajtů|Představuje hodnoty tvořené vysokým celým číslem.|

## <a name="the-void-type"></a>Typ void

**Void** typ je speciální typ; nemůžete deklarovat proměnnou typu **void**, ale můžete deklarovat proměnnou typu `void *` (ukazatel na **void**), což je někdy nezbytné při přidělování nezpracované (netypové) paměti. Nicméně ukazatele na **void** nejsou typově bezpečné a obecně jejich použití je silně nedoporučeno v moderním jazyce C++. V deklaraci funkce **void** návratová hodnota znamená, že funkce nevrátí hodnotu; to je běžné a přijatelné použití typu **void**. Přestože jazyk C vyžaduje funkce, které mají nulové parametry pro deklaraci **void** v seznamu parametrů, třeba `fou(void)`, tato praxe se nedoporučuje v moderním jazyce C++ a by měly být deklarovány `fou()`. Další informace najdete v tématu [převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="const-type-qualifier"></a>Kvalifikátor typu const

Jakýkoli vestavěný nebo uživatelem definovaný typ může být kvalifikován pomocí klíčového slova const. Členské funkce mohou navíc mít **const**-kvalifikovaný a dokonce i **const**-přetížené. Hodnota **const** nelze změnit po inicializaci.

```cpp

const double PI = 3.1415;
PI = .75 //Error. Cannot modify const variable.

```

**Const** kvalifikátor je často používána v deklaracích funkcí a proměnných a "správnost const" je důležitý koncept v jazyce C++; v podstatě znamená použití **const** k zajištění v době kompilace úpravě hodnot. Další informace najdete v tématu [const](../cpp/const-cpp.md).

A **const** se liší od své nekonstantní verze; například **const int** je odlišný od typu **int**. Můžete použít C++ **const_cast** operátor v těch výjimečných případech, kdy je třeba odebrat *const-ness* z proměnné. Další informace najdete v tématu [převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

## <a name="string-types"></a>Typy řetězců

Přesněji řečeno jazyk C++ nemá žádný typ integrované řetězec; **char** a **wchar_t** ukládají jednotlivé znaky – třeba deklarovat více těchto typů aproximace řetězce, přidávání ukončující hodnotu null (například ASCII `'\0'`) k prvku pole za za posledním platným znakem (také nazývané *řetězce ve stylu C*). Psaní řetězců ve stylu C vyžadovalo zapsat mnohem více kódu nebo využít funkce externí knihovny pro tvorbu řetězců. Ale v moderní C++ máme typy standardní knihovny `std::string` (pro 8bitové **char**-řetězce znaků typu) nebo `std::wstring` (pro 16bitové **wchar_t**-řetězce znaků typu). Tyto kontejnery standardní knihovny C++ lze považovat za nativní typy řetězce vzhledem k tomu, že jsou součástí standardní knihovny, které jsou součástí žádné kompatibilní prostředí pro sestavení C++. Jednoduše použít `#include <string>` – direktiva tyto typy dostupné v programu. (Pokud používáte knihovnu MFC nebo ATL, je k dispozici také třída CString, ta ale není součástí standardu C++.) Použití polí znaků zakončených hodnotou null (výše zmíněné řetězce ve stylu C) se v moderním jazyce C++ důrazně nedoporučuje.

## <a name="user-defined-types"></a>Uživateli definované typy

Při definování **třídy**, **struktura**, **sjednocení**, nebo **výčtu**, tato konstrukce použita ve zbytku kódu jako by šlo o základní typ. . Má známou velikost v paměti a na kontrolu doby kompilace a doby trvání programu při běhu se vztahují některá pravidla týkající se způsobu jeho použití. Nejdůležitější rozdíly mezi základními typy a typy definovanými uživateli jsou následující:

- Kompilátor neobsahuje žádné předdefinované informace o uživatelském typu. Pokud se setká poprvé definici během kompilace, učí se typu.

- Jako uživatel určujete, jaké operace lze s vaším typem provádět a jak ho lze převést na další typy. K tomu definujete (pomocí přetížení) příslušné operátory, buď jako členy třídy nebo jako nečlenské funkce. Další informace najdete v tématu [přetížení funkce](function-overloading.md).

- Není nutné zadávat typy staticky (pravidlo, že typ objektu se nikdy nemění). Prostřednictvím mechanismů *dědičnosti* a *polymorfismus*, proměnná definovaná jako uživatelem definovaný typ třídy (dále jako instance objektu třídy) může mít jiný typ v době běhu, než na Doba kompilace. Další informace najdete v tématu [dědičnosti](../cpp/inheritance-cpp.md).

## <a name="pointer-types"></a>Typy ukazatelů

Už od nejstarší verze jazyka C, C++ i nadále umožňuje deklarovat proměnnou typu ukazatel pomocí speciálního deklarátoru `*` (hvězdička). Typ ukazatele ukládá adresu umístění v paměti, kde je uložena skutečná hodnota dat. V moderním jazyce C++, tyto jsou označovány jako *nezpracované ukazatele*a jsou přístupné z kódu pomocí speciálních operátorů `*` (hvězdička) nebo `->` (pomlčka s větší-než). Tento postup se nazývá *přesměrování*, a který z nich použijete, závisí na tom, zda dereferencujete ukazatel na skalár nebo ukazatel na člen v objektu. Práce s typy ukazatelů byla dlouhou dobu jedním z nejsložitějších a nejvíce matoucích aspektů vývoje programů v jazycích C a C++. Tato část popisuje některé skutečnosti a postupy umožňující použití nezpracovaných ukazatele, pokud chcete, ale v moderní C++ již má požadované (nebo doporučené) používat nezpracované ukazatele pro vlastnictví objektu, vzhledem k vývoji [inteligentního ukazatele](../cpp/smart-pointers-modern-cpp.md) () podrobněji na konci této části). Nezpracované ukazatele lze stále s výhodou a bezpečně používat ke sledování objektů, pokud je však potřebujete použít pro vlastnictví objektu, měli byste tak činit s rozvahou a velmi pečlivě promyslet, jak se budou objekty vlastněné těmito ukazateli vytvářet a odstraňovat.

Základní princip, který byste měli znát, je, že deklarací proměnné nezpracovaného ukazatele se přidělí pouze paměť potřebná k uložení adresy umístění v paměti, na které bude ukazatel odkazovat při zrušení reference. Přidělení paměti pro samotnou hodnotu dat (také nazývané *záložní úložiště*) není v tomto okamžiku nepřidělí. Jinými slovy, deklarováním proměnné nezpracovaného ukazatele vytváříte proměnnou adresy v paměti, nikoli skutečnou datovou proměnnou. Zrušení reference na proměnnou ukazatele, aniž byste se ujistili, že proměnná obsahuje platnou adresu záložního úložiště, způsobí v programu nedefinované chování (obvykle závažnou chybu). Následující příklad ukazuje tento druh chyby:

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

Příklad opraveného kódu používá místní zásobník paměti k vytvoření základní úložiště `pNumber` odkazuje na. Pro jednoduchost používáme základní typ. V praxi záložním úložištěm pro ukazatele jsou většinu uživatelem definované typy, které jsou dynamicky přiřazovány do oblasti paměti pojmenované *haldy* (nebo *volné úložiště*) pomocí **nové** výrazu klíčového slova (v programování ve stylu C, starší `malloc()` byla použita funkce knihovny C runtime). Po přidělení, tyto proměnné jsou obvykle označovány jako objekty, zejména v případě, že jsou založeny na definici třídy. Paměť přidělená k **nové** musí být odstraněna odpovídajícím **odstranit** – příkaz (nebo pokud jste použili `malloc()` funkce k přidělení funkce modulu runtime jazyka C `free()`).

Je však snadné zapomenout odstranit dynamicky přiřazované objekty-zejména v komplexním kódu, který způsobí chybu prostředků zvanou *nevracení paměti*. Z tohoto důvodu se používání nezpracovaných ukazatelů v moderním jazyce C++ nedoporučuje. Je téměř vždy lepší využít obtékání ukazatele raw [inteligentního ukazatele](../cpp/smart-pointers-modern-cpp.md), který automaticky uvolní paměť při vyvolání jeho destruktoru (když kód vzroste mimo rozsah pro inteligentní ukazatele); pomocí inteligentních ukazatelů můžete prakticky Eliminujte celé třídy chyb ve vašich programech C++. V následujícím příkladu předpokládejme `MyClass` je uživatelem definovaný typ, který má veřejnou metodu `DoSomeWork();`

```cpp
void someFunction() {
    unique_ptr<MyClass> pMc(new MyClass);
    pMc->DoSomeWork();
}
  // No memory leak. Out-of-scope automatically calls the destructor
  // for the unique_ptr, freeing the resource.
```

Další informace o inteligentních ukazatelích naleznete v tématu [inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md).

Další informace o převodech ukazatelů naleznete v tématu [převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md).

Další informace o ukazatelích obecně naleznete v tématu [ukazatele](../cpp/pointers-cpp.md).

## <a name="windows-data-types"></a>Datové typy ve Windows

V klasickém programování Win32 pro C a C++ většina funkcí používá specifické pro Windows – definice TypeDef a #define makra (definované v `windef.h`) k určení typů parametrů a návratové hodnoty. Tyto datové typy Windows jsou většinou pouze zvláštní názvy (aliasy) na předdefinované typy jazyka C/C++. Úplný seznam těchto – definice TypeDef a definičních souborů preprocesoru naleznete v tématu [datové typy Windows](/windows/desktop/WinProg/windows-data-types). Některé tyto funkce typedef, jako např. HRESULT a LCID, jsou užitečné a mají popisný charakter. Jiné, například INT, nemají zvláštní význam a představují pouze aliasy základních typů jazyka C++. Další datové typy systému Windows si zachovaly názvy pocházející z dob programování v jazyce C a 16bitových procesorů a ve světě moderního hardwaru a operačních systémů již nemají místo ani smysl. Existují také speciální datové typy přidružené ke knihovně Runtime Windows uvedené jako [základní datové typy Windows Runtime](/windows/desktop/WinRT/base-data-types). V moderním jazyce C++ platí obecná rada preferovat základní typy C++, pokud typ Windows nesděluje některý další význam o tom, jak má být daná hodnota interpretována.

## <a name="more-information"></a>Další informace

Další informace o systému typů v jazyce C++ naleznete v následujících tématech.

|||
|-|-|
|[Typy hodnot](../cpp/value-types-modern-cpp.md)|Popisuje *typů hodnot* a problémy týkající se jejich použití.|
|[Převody a bezpečnost typů](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Popisuje běžné problémy při převodu typů a ukazuje, jak se jim vyhnout.|

## <a name="see-also"></a>Viz také:

[C++ vás vítá zpět](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)<br/>
[Standardní knihovna C++](../standard-library/cpp-standard-library-reference.md)