---
title: Standardní převody
ms.date: 11/04/2016
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: 7a42a4f35a29489fe23327c6b34ed49197a64724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575445"
---
# <a name="standard-conversions"></a>Standardní převody

Jazyk C++ definuje převody mezi základními typy. Definuje také převody pro ukazatel, odkaz a pro odvozené typy ukazatele na člena. Tyto převody jsou označovány jako *standardní převody*.

Tato část popisuje následující standardní převody:

- Integrální povýšení

- Integrální převody

- Převody s plovoucí desetinnou čárkou

- Převody s plovoucí desetinnou čárkou a integrální převody

- Aritmetické převody

- Převody ukazatele

- Převody odkazů

- Převody ukazatele na člena

    > [!NOTE]
    >  Uživatelské typy mohou zadat své vlastní převody. Převod uživatelských typů je obsažen v [konstruktory](../cpp/constructors-cpp.md) a [převody](../cpp/user-defined-type-conversions-cpp.md).

Následující kód provede převody (v tomto příkladu integrální povýšení):

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Výsledkem převodu je l-hodnota pouze v případě, že vytvoří typ odkazu. Například uživatelem definovaný převod deklarovaný jako `operator int&()` vrátí odkaz a je l hodnotou. Ale převod deklarovaný jako `operator int()`vrátí objekt a není l hodnotou.

## <a name="integral-promotions"></a>Integrální povýšení

Objekty celočíselného typu lze převést na jiné širší celočíselné typy (to znamená na typy, které mohou představovat větší množinu hodnot). Tento typ rozšiřujícího převodu se nazývá „povýšení celočíselného typu“. S povýšením celočíselného typu lze všude ve výrazu, kde lze použít jiný celočíselný typ, použít následující:

- Objekty, literály a konstanty typu **char** a **krátká celočíselná**

- Výčtové typy

- **int** bitová pole

- Enumerátory

Povýšení typu v jazyce C++ „zachovávají hodnotu“. To znamená, že hodnota po povýšení zůstane stejná jako hodnota před povýšením. V zachovávajícího hodnotu, objekty kratších celočíselných typů (jako je například bitová pole nebo objekty typu **char**) jsou povýšeny na typ **int** Pokud **int** může představovat úplnou rozsah z původního typu. Pokud **int** nemůže reprezentovat úplný rozsah hodnot, pak je objekt povýšen na typ **unsigned int**. Ačkoli je tato strategie stejná jako ve standardu ANSI C, převody zachovávající hodnotu nezachovávají to, zda objekt má nebo nemá znaménko.

Povýšení typu zachovávající hodnotu a povýšení typu, která normálně zachovávají znaménko, vrátí stejné výsledky. Mohou však vrátit různé výsledky, pokud je povýšený typ objektu jedním z následujících:

- Operand operátoru **/**, `%`, `/=`, `%=`, **<**, **\< =**, **>**, nebo **>=**

   Tyto operátory spoléhají pro stanovení výsledku na znaménko. Proto povýšení typu zachovávající hodnotu a povýšení typu zachovávající znaménko vrátí při použití s těmito operandy různé výsledky.

- Levý operand **>>** nebo **>>=**

   Tyto operátory zacházejí při provádění operací posunu s hodnotami se znaménkem nebo bez znaménka odlišně. U hodnot se znaménkem posunutí hodnoty vpravo způsobí, že je bit znaménka posunut na pozici uvolněného bitu. U hodnot bez znaménka jsou pozice uvolněných bitů vyplněny nulami.

- Argument přetížené funkce nebo operand přetíženého operátoru, který závisí na tom, zda je typ tohoto operandu pro párování argumentů se znaménkem nebo bez. (Viz [přetížené operátory](../cpp/operator-overloading.md) Další informace o definici přetížených operátorů.)

## <a name="integral-conversions"></a>Integrální převody

Mezi celočíselnými typy jsou prováděny celočíselné převody. Integrální typy jsou **char**, **int**, a **dlouhé** (a **krátký**, **podepsané**a **bez znaménka** verze těchto typů).

**Podepsaného na nepodepsané**

Objekty celočíselných typů se znaménkem lze převést na odpovídající typy bez znaménka. Když tyto převody nastanou, skutečný bitový vzor se nezmění. Změní se však interpretace dat. Vezměte v úvahu tento kód:

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

V předchozím příkladu **podepsané řečeno**, `i`, je definována a inicializována na záporné číslo. Výraz `(u = i)` způsobí, že `i` pro převod na **unsigned short** před přiřazením k `u`.

**Unsigned na signed**

Objekty celočíselných typů bez znaménka lze převést na odpovídající typy se znaménkem. Avšak takový převod může způsobit špatné vyhodnocení dat, je-li hodnota objektu bez znaménka mimo rozsah reprezentovatelný typem se znaménkem, jak je uvedeno v následujícím příkladu:

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

V předchozím příkladu `u` je **unsigned short** celočíselný objekt, který musí být převeden na hodnotu se znaménkem pro vyhodnocení výrazu `(i = u)`. Vzhledem k tomu, že jeho hodnotu nelze vyjádřit správně **podepsané řečeno**, data chybně interpretována, jak je znázorněno.

## <a name="floating-point-conversions"></a>Plovoucí převody bodu

Objekt typu s plovoucí desetinnou čárkou lze bezpečně převést na přesnější typ s plovoucí desetinnou čárkou, to znamená, že převod nezpůsobí ztrátu významu. Například převody z **float** k **double** nebo z **double** k **long double** jsou bezpečné a hodnota se nezmění.

Objekt typu s plovoucí desetinnou čárkou lze převést na méně přesný typ, pokud je v rozsahu vyjádřitelném tímto typem. (Viz [plovoucí omezení](../cpp/floating-limits.md) pro rozsahy typů s plovoucí desetinnou čárkou.) Pokud nelze původní hodnotu přesně vyjádřit, může být převedena buď na další vyšší, nebo na další nižší vyjádřitelnou hodnotu. Pokud žádná taková hodnota neexistuje, výsledek není definován. Vezměte v úvahu v následujícím příkladu:

```cpp
cout << (float)1E300 << endl;
```

Maximální hodnota vyjádřitelná typem **float** je 3.402823466E38 – je mnohem menší hodnota než 1E300. Proto číslo je převedeno na nekonečno a výsledek je "informace".

## <a name="conversions-between-integral-and-floating-point-types"></a>Převody mezi typy s plovoucí desetinnou čárkou a integrální bodů

Určité výrazy mohou způsobit převod objektů typu s plovoucí desetinnou čárkou na celočíselné typy nebo naopak. Jakmile je objekt celočíselného typu převeden na typ s plovoucí desetinnou čárkou a původní hodnotu nelze převést zcela přesně, výsledkem je nejbližší vyšší nebo nejbližší nižší reprezentovatelná hodnota.

Při převodu objektu typu s plovoucí desetinnou čárkou na celočíselný typ je desetinná část zkrácena. V procesu převodu se neuskuteční zaokrouhlení. Zkrácení znamená, že číslo 1,3 je převedeno na hodnotu 1 a-1.3 je převedena na hodnotu -1.

## <a name="arithmetic-conversions"></a>Aritmetické převody

Mnoho binárních operátorů (popsáno v [výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)) způsobuje převody operandů a vrací výsledky stejným způsobem. Způsob, jakým tyto operátory provádějí převody, se nazývá „obvyklé aritmetické převody“. Aritmetické převody operandů různých nativních typů jsou prováděny tak, jak je znázorněno v následující tabulce. Typy typedef se chovají podle svých základních nativních typů.

### <a name="conditions-for-type-conversion"></a>Podmínky pro převod typu

|Splněné podmínky|Převod|
|--------------------|----------------|
|Některý operand je typu **long double**.|Další operand je převeden na typ **long double**.|
|Předcházející podmínky nebyly splněny a některý operand je typu **double**.|Další operand je převeden na typ **double**.|
|Předcházející podmínky nebyly splněny a některý operand je typu **float**.|Další operand je převeden na typ **float**.|
|Předcházející podmínky nebyly splněny (žádný z operandů není typ s plovoucí desetinnou čárkou).|Celočíselné povýšení je s těmito operandy provedeno následovně:<br /><br />– Pokud některý operand je typu **unsigned long**, je druhý operand je převeden na typ **unsigned long**.<br />-Pokud není předcházející podmínka splněna a některý operand je typu **dlouhé** a druhý operand typu **unsigned int**, jsou oba operandy převedeny na typ **unsigned long**.<br />– Pokud nejsou splněny obě předcházející podmínky, a pokud některý operand je typu **dlouhé**, je druhý operand je převeden na typ **dlouhé**.<br />– Nejsou-li předchozí tři podmínky splněny a některý operand je typu **unsigned int**, je druhý operand je převeden na typ **unsigned int**.<br />– Pokud je splněna žádná z předchozích podmínek, jsou oba operandy převedeny na typ **int**.|

Následující kód znázorňuje pravidla převodu, která jsou popsána v tabulce:

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

První příkaz v předchozím příkladu znázorňuje násobení dvou celočíselných typů, `iVal` a `ulVal`. Podmínka je splněna, že ani jeden operand není typu s plovoucí desetinnou čárkou a jeden operand je typu **unsigned int**. Proto je druhý operand, `iVal`, je převeden na typ **unsigned int**. Výsledek je přiřazen do proměnné `dVal`. Podmínka je splněna jeden operand je typu **double**, proto **unsigned int** výsledek násobení je převeden na typ **double**.

Druhý příkaz v předchozím příkladu znázorňuje sečtení typu **float** a celočíselného typu, `fVal` a `ulVal`. `ulVal` Proměnná je převeden na typ **float** (třetí podmínka v tabulce). Výsledek součtu je převeden na typ **double** (druhá podmínka v tabulce) a přiřazená `dVal`.

## <a name="pointer-conversions"></a>Převody ukazatele

Ukazatele lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech.

### <a name="pointer-to-classes"></a>Ukazatele na třídy

Existují dva případy, ve kterých lze převést ukazatel na třídu na ukazatel na základní třídu.

První případem je, pokud zadaná základní třída je přístupná a převod je jednoznačný. (Viz [více základních tříd](../cpp/multiple-base-classes.md) Další informace o odkazech na nejednoznačný základní třídy.)

Určuje, zda je dostupná základní třídu, závisí na druh dědičnosti používaných pro odvození. Vezměte v úvahu dědičnosti znázorněné na následujícím obrázku.

![Graf dědičnosti, který znázorňuje základní&#45;třídy usnadnění](../cpp/media/vc38xa1.gif "vc38XA1") grafu dědičnosti pro usnadnění obrázek základní třídy

V následující tabulce jsou uvedeny základní třídy usnadnění pro situace znázorněna na obrázku.

### <a name="base-class-accessibility"></a>Usnadnění základní třídy

|Typ funkce|Odvození|Převod z<br /><br /> B * a\* právní?|
|----------------------|----------------|-------------------------------------------|
|Externí funkce (není třída s rozsahem)|Soukromé|Ne|
||Chráněno|Ne|
||Public|Ano|
|Členská funkce B (v oboru B)|Soukromé|Ano|
||Chráněno|Ano|
||Public|Ano|
|Členská funkce jazyka C (v oboru C)|Soukromé|Ne|
||Chráněno|Ano|
||Public|Ano|

Druhý případ, ve kterém lze převést ukazatel na třídu na ukazatel na základní třídu je při použití explicitní převod typu. (Viz [operátor převodu explicitního typu](explicit-type-conversion-operator-parens.md) pro další informace o převodu explicitního typu.)

Výsledek takového převodu je ukazatel na "podobjekt," část objektu, který je zcela popsal základní třídy.

Následující kód definuje dvě třídy `A` a `B`, kde `B` je odvozen z `A`. (Další informace o dědičnosti, naleznete v tématu [odvozené třídy](../cpp/inheritance-cpp.md).) Potom definuje `bObject`, objekt typu `B`a dva ukazatele (`pA` a `pB`), které ukazují na objekt.

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

Ukazatel `pA` je typu `A *`, což může být interpretován jako význam "ukazatel na objekt typu `A`." Členové `bObject` `(`například `BComponent` a `BMemberFunc`) jsou jedinečné pro typ `B` a proto jsou přístupná přes `pA`. `pA` Ukazatel umožňuje přístup jenom k těmto vlastnostem (členské funkce a data) objektu, které jsou definovány ve třídě `A`.

### <a name="pointer-to-function"></a>Ukazatel na funkci

Ukazatel na funkci lze převést na typ `void *`, pokud typ `void *` je příliš velká pro tento ukazatel.

### <a name="pointer-to-void"></a>Ukazatel na typ void

Ukazatele na typ **void** lze převést na ukazatele na libovolný typ, ale pouze pomocí přetypování explicitního typu (na rozdíl od v jazyce C). Ukazatel na libovolný typ může být implicitně převést na ukazatel na typ **void**. Ukazatel na neúplný objekt typu lze převést na ukazatel na **void** (implicitně) a zpět (explicitně). Výsledek takového převodu je roven hodnotě původního ukazatele. Objekt je považován za neúplný, pokud je deklarovaný, ale není k dispozici dostatek informací, na základě kterých lze určit jeho velikost nebo základní třídu.

Ukazatel na libovolný objekt, který není **const** nebo **volatile** lze implicitně převést na ukazatel typu `void *`.

### <a name="const-and-volatile-pointers"></a>ukazatelé const a volatile

Jazyk C++ neposkytuje standardní převod z **const** nebo **volatile** typu na typ, který není **const** nebo **volatile**. Libovolné druhy převodu lze však určit pomocí přetypování explicitních typů (včetně převodů, které nejsou bezpečné).

> [!NOTE]
>  Ukazatele na členy jazyka C++, s výjimkou ukazatelů na statické členy, jsou odlišné od běžných ukazatelů a nemají stejné standardní převody. Ukazatele na statické členy jsou normální ukazatele a mají stejné převody jako normální ukazatele.

### <a name="null-pointer-conversions"></a>převody ukazatele s hodnotou Null

Celočíselný konstantní výraz, který se vyhodnotí na hodnotu nula nebo takový výraz přetypovaný na typ ukazatele, je převeden na ukazatel zvaný "nulový ukazatel". Tento ukazatel zaručuje nerovnost při porovnání s ukazatelem na libovolný platný objekt nebo funkci (kromě ukazatelů na objekty se základem, které mohou mít stejný posun a stále ukazovat na různé objekty).

V C ++ 11 [nullptr](../cpp/nullptr.md) typ by měl být upřednostňované C-style ukazatel s hodnotou null.

### <a name="pointer-expression-conversions"></a>Převody ukazatele výraz

Každý výraz typu pole lze převést na ukazatel stejného typu. Výsledkem převodu je ukazatel na první prvek pole. Následující příklad ukazuje takový převod:

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Výraz, jehož výsledkem je funkce vracející určitý typ, je převeden na ukazatel na funkci vracející tento typ kromě těchto případů:

- Výraz je použit jako operand operátoru address-of (**&**).

- Výraz je použit jako operand operátoru volání funkce.

## <a name="reference-conversions"></a>Převody odkazů

Odkaz na třídu lze převést na odkaz na základní třídu v následujících případech:

- Zadaná základní třída je přístupná.

- Převod je jednoznačný. (Viz [více základních tříd](../cpp/multiple-base-classes.md) Další informace o odkazech na nejednoznačný základní třídy.)

Výsledkem převodu je ukazatel na podobjekt, který představuje základní třídu.

## <a name="pointer-to-member"></a>Ukazatel na člena

Ukazatele na členy třídy lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech. Tato část popisuje následující převody ukazatele na člen:

## <a name="pointer-to-base-class-member"></a>Ukazatel na člena základní třídy

Ukazatel na člen základní třídy lze převést na ukazatel na člen třídy z ní odvozené, pokud jsou splněny následující podmínky:

- Inverzní převod z ukazatele na odvozenou třídu na ukazatel na základní třídu je přístupný.

- Odvozená třída virtuálně nedědí ze základní třídy.

Je-li levý operand ukazatel na člen, pravý operand musí být typu ukazatele na člen nebo konstantní výraz, který je vyhodnocen na hodnotu 0. Toto přiřazení je platné pouze v následujících případech:

- Pravý operand je ukazatel na člen stejné třídy jako levý operand.

- Levý operand je ukazatel na člen třídy odvozené veřejně a jednoznačně z třídy pravého operandu.

## <a name="integral-constant-conversions"></a>Integrální konstantní konverze

Celočíselný konstantní výraz, který je vyhodnocen na hodnotu nula, je převeden na ukazatel zvaný „nulový ukazatel“. Tento ukazatel zaručuje nerovnost při porovnání s ukazatelem na libovolný platný objekt nebo funkci (kromě ukazatelů na objekty se základem, které mohou mít stejný posun a stále ukazovat na různé objekty).

Následující kód znázorňuje definici ukazatele na člen `i` třídy `A`. Ukazatel `pai` je inicializován na hodnotu 0, což je nulový ukazatel.

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C++](../cpp/cpp-language-reference.md)