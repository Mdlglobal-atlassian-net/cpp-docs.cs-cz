---
title: Standardní převody
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: c51a5ea5aaabb27babb9e4cd355721742088d31e
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998895"
---
# <a name="standard-conversions"></a>Standardní převody

Jazyk C++ definuje převody mezi základními typy. Definuje také převody pro ukazatel, odkaz a pro odvozené typy ukazatele na člena. Tyto převody se nazývají *standardní převody*.

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
  > Uživatelské typy mohou zadat své vlastní převody. Převod uživatelsky definovaných typů je popsaný v části [konstruktory](../cpp/constructors-cpp.md) a [převody](../cpp/user-defined-type-conversions-cpp.md).

Následující kód provede převody (v tomto příkladu integrální povýšení):

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Výsledkem převodu je l-hodnota pouze v případě, že vytvoří typ odkazu. Například uživatelsky definovaný převod deklarovaný jako `operator int&()` vrací odkaz a je l-hodnotou. Převod deklarovaný jako `operator int()` však vrátí objekt a není l-hodnotou.

## <a name="integral-promotions"></a>Integrální povýšení

Objekty integrálního typu lze převést na jiný širší celočíselný typ, tj. typ, který může představovat větší sadu hodnot. Tento typ rozšiřování konverze se nazývá *integrální povýšení*. Při povýšení integrálního typu můžete použít následující typy ve výrazu bez ohledu na to, kde je možné použít jiný integrální typ:

- Objekty, literály a konstanty typu **char** a **short int**

- Výčtové typy

- bitové pole **int**

- Enumerátory

C++propagační akce jsou "zachování hodnoty", jako hodnota po povýšení, která je zaručena jako hodnota před povýšením. U propagačních akcí, které zachovává hodnoty, jsou objekty kratších integrálních typů (například bitových polí nebo objektů typu **char**) povýšeny na typ **int** , pokud **int** může představovat plný rozsah původního typu. Pokud **int** nemůže reprezentovat plný rozsah hodnot, pak je objekt povýšen na typ **unsigned int**.  I když je tato strategie stejná jako ta, kterou používá standardní C, převody bez obsluhy nezachovávají "podepsané" objektu.

Povýšení typu zachovávající hodnotu a povýšení typu, která normálně zachovávají znaménko, vrátí stejné výsledky. Můžou ale způsobit různé výsledky, pokud se propagovaný objekt zobrazí jako:

- Operand `/`, `%`, `/=`, `%=`, `<`, `<=`, `>`nebo `>=`

   Tyto operátory spoléhají pro stanovení výsledku na znaménko. Zachování hodnot a zachovávání nabídek při použití na tyto operandy vytváří různé výsledky.

- Levý operand `>>` nebo `>>=`

   Tyto operátory se v rámci operace posunu považovat za jiné množství znaménka a nepodepsaného. U podepsaných množství je operace pravého posunutí propagována bit znaménka do uvolněné bitových pozic, zatímco uvolněné bitové pozice jsou vyplněna nulami v nepodepsaných množstvích.

- Argument přetížené funkce nebo operand přetíženého operátoru, který závisí na znaménku typu operandu pro porovnání argumentů. Další informace o definování přetížených operátorů naleznete v tématu [přetížené operátory](../cpp/operator-overloading.md).

## <a name="integral-conversions"></a>Integrální převody

*Celočíselné převody* jsou převody mezi celočíselnými typy. Integrální typy jsou **char**, **short** (nebo **short int**), **int**, **Long**a **Long Long**. Tyto typy mohou být kvalifikovány **se znaménkem nebo** **bez** **znaménka a nelze** je použít jako zkratku pro **celé číslo bez znaménka**.

### <a name="signed-to-unsigned"></a>Podepsáno na nepodepsané

Objekty celočíselných typů se znaménkem lze převést na odpovídající typy bez znaménka. Když dojde k těmto převodům, skutečný bitový vzorek se nezmění. Nicméně výklad dat se změní. Vezměte v úvahu tento kód:

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

V předchozím příkladu je **znaménko short**, `i`, definováno a inicializováno na záporné číslo. Výraz `(u = i)` způsobí, že `i` převést na **znaménko short** před přiřazením `u`.

### <a name="unsigned-to-signed"></a>Nepodepsané na signed

Objekty celočíselných typů bez znaménka lze převést na odpovídající typy se znaménkem. Pokud je však hodnota bez znaménka mimo reprezentovatelné rozsah podepsaného typu, výsledek nebude mít správnou hodnotu, jak je znázorněno v následujícím příkladu:

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

V předchozím příkladu `u` je **nepodepsaný krátký** integrálový objekt, který musí být převeden na znaménko množství pro vyhodnocení `(i = u)`výrazů. Vzhledem k tomu, že jeho hodnota nemůže být správně reprezentovaná v **signed short**, data jsou nesprávně interpretována, jak je znázorněno.

## <a name="floating-point-conversions"></a>Převody s plovoucí desetinnou čárkou

Objekt typu s plovoucí desetinnou čárkou lze bezpečně převést na přesnější typ s plovoucí desetinnou čárkou, to znamená, že převod nezpůsobí ztrátu významu. Například převod z **float** na **Double** nebo z **Double** na **Long Double** je bezpečný a hodnota je beze změny.

Objekt plovoucího typu lze také převést na méně přesný typ, pokud je v rozsahu, který je reprezentován tímto typem. (Viz [omezení plovoucí](../cpp/floating-limits.md) pro rozsahy plovoucích typů.) Pokud původní hodnota není reprezentována přesně, může být převedena na další vyšší nebo na další nižší reprezentovatelné hodnoty. Výsledek není definován, pokud taková hodnota neexistuje. Vezměte v úvahu v následujícím příkladu:

```cpp
cout << (float)1E300 << endl;
```

Maximální hodnota, která je reprezentována typem **float** , je 3.402823466 E38 – mnohem menší číslo než 1E300. Proto je číslo převedeno na nekonečno a výsledek je "INF".

## <a name="conversions-between-integral-and-floating-point-types"></a>Převody mezi typy integrálních a plovoucích bodů

Určité výrazy mohou způsobit převod objektů typu s plovoucí desetinnou čárkou na celočíselné typy nebo naopak. Když je objekt integrálního typu převeden na plovoucí typ a původní hodnota není reprezentována přesně, výsledek je následující vyšší nebo další nižší reprezentovatelné hodnoty.

Když je objekt plovoucího typu převeden na celočíselný typ, Zlomková část je *zkrácena*nebo zaokrouhlena směrem k nule. Číslo, jako je 1,3, je převedeno na 1 a-1,3 je převedeno na-1. Pokud je zkrácená hodnota vyšší než nejvyšší reprezentovatelné hodnoty nebo nižší než nejnižší reprezentující hodnota, výsledek není definován.

## <a name="arithmetic-conversions"></a>Aritmetické převody

Mnoho binárních operátorů (popsaných v tématu [výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)) způsobuje převody operandů a výsledky jsou stejné jako. Převody, které tyto operátory způsobují, se nazývají *běžné aritmetické převody*. Aritmetické převody operandů, které mají různé nativní typy, jsou provedeny, jak je uvedeno v následující tabulce. Typy typedef se chovají podle svých základních nativních typů.

### <a name="conditions-for-type-conversion"></a>Podmínky pro převod typu

|Splněné podmínky|Konverze|
|--------------------|----------------|
|Buď je operand typu **Long Double**.|Další operand je převeden na typ **Long Double**.|
|Předchozí podmínka není splněna a jeden operand je typu **Double**.|Další operand je převeden na typ **Double**.|
|Předchozí podmínky nejsou splněné a jeden operand je typu **float**.|Další operand je převeden na typ **float**.|
|Předcházející podmínky nebyly splněny (žádný z operandů není typ s plovoucí desetinnou čárkou).|Operandy získají celočíselné propagační akce následujícím způsobem:<br /><br />– Pokud je jeden operand typu **bez znaménka Long**, je druhý operand převeden na typ **bez znaménka Long**.<br />– Pokud předchozí podmínka není splněna a pokud je jeden z operandů typu **Long** a druhý typu **bez znaménka int**, jsou oba operandy převedeny na typ **bez znaménka Long**.<br />– Pokud nejsou splněny předchozí dvě podmínky a pokud je jeden z operandů typu **Long**, je druhý operand převeden na typ **Long**.<br />– Pokud nejsou splněny předchozí tři podmínky, a pokud je jeden z operandů typu **bez znaménka int**, je druhý operand převeden na typ **int bez znaménka**.<br />– Pokud není splněna žádná z předchozích podmínek, jsou oba operandy převedeny na typ **int**.|

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

První příkaz v předchozím příkladu znázorňuje násobení dvou celočíselných typů, `iVal` a `ulVal`. Podmínka splněná je v tom, že ani operand není typu float, a jeden operand je typu **unsigned int**. Druhý operand, `iVal`, je tedy převeden na typ **unsigned int**. Výsledek se pak přiřadí `dVal`. Podmínka, která je zde splněna, je, že jeden operand je typu **Double**, takže výsledek násobení **unsigned int** je převeden na typ **Double**.

Druhý příkaz v předchozím příkladu ukazuje přidání typu **float** a integrálního typu: `fVal` a `ulVal`. Proměnná `ulVal` je převedena na typ **float** (třetí podmínka v tabulce). Výsledek sčítání je převeden na typ **Double** (druhá podmínka v tabulce) a přiřazeno k `dVal`.

## <a name="pointer-conversions"></a>Převody ukazatele

Ukazatele lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech.

### <a name="pointer-to-classes"></a>Ukazatel na třídy

Existují dva případy, kdy je možné ukazatel na třídu převést na ukazatel na základní třídu.

První případ je v případě, že je zadaná základní třída přístupná a převod je nejednoznačný. Další informace o nejednoznačných odkazech na základní třídu naleznete v tématu [více základních tříd](../cpp/multiple-base-classes.md).

Zda je základní třída přístupná, závisí na druhu dědičnosti použitých v odvození. Zvažte dědění na následujícím obrázku.

![Graf dědičnosti znázorňující&#45;]přístupnost základní třídy(../cpp/media/vc38xa1.gif "zobrazení grafu dědičnosti základní&#45;třídy") <br/>
Graf dědičnosti pro ilustraci usnadnění základní třídy

Následující tabulka ukazuje přístupnost základní třídy pro situaci, která je znázorněna na obrázku.

|Typ funkce|Odvození|Převod z<br /><br /> B * do\* legální?|
|----------------------|----------------|-------------------------------------------|
|Externí funkce (není v oboru tříd)|Soukromé|Ne|
||chráněný|Ne|
||Public|Ano|
|B – členská funkce (v oboru B)|Soukromé|Ano|
||chráněný|Ano|
||Public|Ano|
|Členská funkce jazyka c (v oboru C)|Soukromé|Ne|
||chráněný|Ano|
||Public|Ano|

Druhý případ, ve kterém může být ukazatel na třídu převeden na ukazatel na základní třídu, je při použití explicitní konverze typu. Další informace o explicitních převodech typů naleznete v tématu [operátor převodu explicitního typu](explicit-type-conversion-operator-parens.md).

Výsledek takového převodu je ukazatel na *podobjekt*, část objektu, která je zcela popsána základní třídou.

Následující kód definuje dvě třídy, `A` a `B`, kde `B` je odvozeno od `A`. (Další informace o dědičnosti naleznete v tématu [odvozené třídy](../cpp/inheritance-cpp.md).) Pak definuje `bObject`, objekt typu `B`a dva ukazatele (`pA` a `pB`), které odkazují na objekt.

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

Ukazatel `pA` je typu `A *`, který může být interpretován jako "ukazatel na objekt typu `A`." Členové `bObject` (například `BComponent` a `BMemberFunc`) jsou jedinečné pro typ `B` a jsou proto nepřístupné prostřednictvím `pA`. Ukazatel `pA` umožňuje přístup pouze k těmto charakteristikám (členské funkce a data) objektu, které jsou definovány ve třídě `A`.

### <a name="pointer-to-function"></a>Ukazatel na funkci

Ukazatel na funkci lze převést na typ `void *`, pokud je typ `void *` dostatečně velký pro uložení tohoto ukazatele.

### <a name="pointer-to-void"></a>Ukazatel na void

Ukazatele na typ **void** lze převést na ukazatele na jakýkoli jiný typ, ale pouze s přetypováním explicitního typu (na rozdíl od jazyka C). Ukazatel na libovolný typ lze převést implicitně na ukazatel na typ **void**. Ukazatel na nekompletní objekt typu lze převést na ukazatel na **typ void** (implicitně) a zpět (explicitně). Výsledek takového převodu je roven hodnotě původního ukazatele. Objekt se považuje za nekompletní, pokud je deklarovaný, ale k dispozici nejsou dostatečné informace k určení jeho velikosti nebo základní třídy.

Ukazatel na libovolný objekt, který není **const** nebo **volatile** , lze implicitně převést na ukazatel typu `void *`.

### <a name="const-and-volatile-pointers"></a>const a volatile – ukazatele

C++nedodá standardní převod z typu **const** nebo **volatile** na typ, který není **const** nebo **volatile**. Libovolné druhy převodu lze však určit pomocí přetypování explicitních typů (včetně převodů, které nejsou bezpečné).

> [!NOTE]
> C++ukazatele na členy, s výjimkou ukazatelů na statické členy, se liší od normálních ukazatelů a nemají stejné standardní převody. Ukazatele na statické členy jsou normální ukazatele a mají stejné převody jako normální ukazatele.

### <a name="null-pointer-conversions"></a>nenulové převody ukazatelů

Celočíselný konstantní výraz, který je vyhodnocen jako nula, nebo takové přetypování výrazu na typ ukazatele, je převeden na ukazatel nazvaný *ukazatel s hodnotou null*. Tento ukazatel vždy porovnává nerovnost s ukazatelem na libovolný platný objekt nebo funkci. Výjimkou jsou ukazatele na objekty založené na objektech, které mohou mít stejný posun a pořád odkazují na různé objekty.

V jazyce C++ 11 by měl být typ [nullptr](../cpp/nullptr.md) upřednostňovaný na ukazatel null ve stylu jazyka C.

### <a name="pointer-expression-conversions"></a>Převody výrazů ukazatelů

Každý výraz typu pole lze převést na ukazatel stejného typu. Výsledkem převodu je ukazatel na první prvek pole. Následující příklad ukazuje takový převod:

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Výraz, jehož výsledkem je funkce vracející určitý typ, je převeden na ukazatel na funkci vracející tento typ kromě těchto případů:

- Výraz je použit jako Operand operátoru address-of ( **&** ).

- Výraz je použit jako operand operátoru volání funkce.

## <a name="reference-conversions"></a>Převody odkazů

Odkaz na třídu lze převést na odkaz na základní třídu v těchto případech:

- Zadaná základní třída je přístupná.

- Převod je jednoznačný. (Další informace o nejednoznačných odkazech na základní třídu naleznete v tématu [více základních tříd](../cpp/multiple-base-classes.md).)

Výsledkem převodu je ukazatel na podobjekt, který představuje základní třídu.

## <a name="pointer-to-member"></a>Ukazatel na člena

Ukazatele na členy třídy lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech. Tato část popisuje následující převody ukazatele na člen:

### <a name="pointer-to-base-class-member"></a>Ukazatel na člena základní třídy

Ukazatel na člen základní třídy lze převést na ukazatel na člen třídy z ní odvozené, pokud jsou splněny následující podmínky:

- Inverzní převod z ukazatele na odvozenou třídu na ukazatel na základní třídu je přístupný.

- Odvozená třída virtuálně nedědí ze základní třídy.

Je-li levý operand ukazatel na člen, pravý operand musí být typu ukazatele na člen nebo konstantní výraz, který je vyhodnocen na hodnotu 0. Toto přiřazení je platné pouze v následujících případech:

- Pravý operand je ukazatel na člen stejné třídy jako levý operand.

- Levý operand je ukazatel na člen třídy odvozené veřejně a jednoznačně z třídy pravého operandu.

### <a name="null-pointer-to-member-conversions"></a>nulový ukazatel na převody členů

Celočíselný konstantní výraz, který je vyhodnocen jako nula, je převeden na ukazatel s hodnotou null. Tento ukazatel vždy porovnává nerovnost s ukazatelem na libovolný platný objekt nebo funkci. Výjimkou jsou ukazatele na objekty založené na objektech, které mohou mít stejný posun a pořád odkazují na různé objekty.

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

[C++Referenční dokumentace jazyka](../cpp/cpp-language-reference.md)