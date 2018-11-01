---
title: Používání operátorů insertion a řízení formátu
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 8c04cc6d5deeaf5dfea65a7f8e92a8569084c077
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565409"
---
# <a name="using-insertion-operators-and-controlling-format"></a>Používání operátorů insertion a řízení formátu

Toto téma ukazuje, jak řídit formát a jak vytvořit operátorů insertion pro vaše vlastní třídy. Vložení (**<<**) operátor, který je předem naprogramovaných pro všechny datové typy standard C++, odešle do výstupní objekt datového proudu bajtů. Operátorů insertion pracovat s předdefinovanou "manipulátory,", které jsou prvky, které Změna výchozího formátu celočíselné argumenty.

Můžete řídit formát s následujícími možnostmi:

- [Šířka výstupu](#vclrfoutputwidthanchor3)

- [Zarovnání](#vclrfalignmentanchor4)

- [Přesnost](#vclrfprecisionanchor5)

- [Radix](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a> Šířka výstupu

Zarovnat výstup, určíte tak, že šířka výstupu pro každou položku `setw` manipulátor v datovém proudu nebo voláním `width` členskou funkci. V tomto příkladu vpravo – zarovná hodnoty ve sloupci minimálně 10 znaků široký:

```cpp
// output_width.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   for( int i = 0; i < 4; i++ )
   {
      cout.width(10);
      cout << values[i] << '\n';
   }
}
```

```Output
      1.23
     35.36
     653.7
   4358.24
```

Počátečními nulami přidají na libovolnou hodnotu míň než 10 znaků na šířku.

K vyplnění pole, použijte `fill` členskou funkci, která nastaví hodnotu pro pole, která mají nastavená Šířka znaku odsazení. Výchozí hodnota je prázdné. Pro vyplnění sloupce čísel hvězdičkami, upravit předchozí **pro** smyčky následujícím způsobem:

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

`endl` Manipulátor nahradí znak nového řádku (`'\n'`). Výstup vypadá takto:

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

Pokud chcete zadat šířku datových prvků na stejném řádku, použijte `setw` manipulátor:

```cpp
// setw.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };
   for( int i = 0; i < 4; i++ )
      cout << setw( 7 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

`width` Členská funkce je deklarována v \<iostream – >. Pokud používáte `setw` nebo jakékoli jiné manipulátor s argumenty, je nutné zahrnout \<iomanip >. Ve výstupu jsou řetězce vytištěn v pole šířky 6 a celá čísla v poli šířky 10:

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

Ani `setw` ani `width` zkrátí hodnoty. Pokud formátovaný výstup přesahuje šířku, vytiskne celou hodnotu v souladu s přesností nastavení datového proudu. Obě `setw` a `width` ovlivňují jenom následující pole. Šířka pole se vrátí do jeho výchozí chování (nezbytná šířka) po vytisknutí jedno pole. Však další možnosti formátu datového proudu zůstávají v platnosti až do změnit.

## <a name="vclrfalignmentanchor4"></a> Zarovnání

Výstupní datové proudy výchozí text zarovnaný vpravo. Názvy v předchozím příkladu zarovnání doleva a čísel Zarovnat doprava, nahraďte **pro** smyčky následujícím způsobem:

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

Výstup vypadá takto:

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

Příznak left-align je nastaven pomocí [setiosflags](../standard-library/iomanip-functions.md#setiosflags) manipulátor s `left` enumerátor. Tento výčet je definován v [ios](../standard-library/basic-ios-class.md) třídy, proto musí obsahovat svůj odkaz **ios::** předponu. [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) manipulátor vypne left-align příznak. Na rozdíl od `width` a `setw`, účinek `setiosflags` a `resetiosflags` je trvalá.

## <a name="vclrfprecisionanchor5"></a> Přesnost

Výchozí hodnota pro přesnost s plovoucí desetinnou čárkou je šest. Například číslo 3466.9768 vytiskne jako 3466.98. Chcete-li změnit způsob, jakým vytiskne tuto hodnotu, použijte [setprecision](../standard-library/iomanip-functions.md#setprecision) manipulátor. Manipulátor má dva příznaky: [oprava](../standard-library/ios-functions.md#fixed) a [vědecké](../standard-library/ios-functions.md#scientific). Pokud [oprava](../standard-library/ios-functions.md#fixed) nastavena číslo vytiskne jako 3466.976800. Pokud `scientific` je nastaven, vytiskne jako 3.4669773 + 003.

Chcete-li zobrazit číslo s plovoucí desetinnou čárkou uvedené v [zarovnání](#vclrfalignmentanchor4) jednu číslici, nahradit **pro** smyčky následujícím způsobem:

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6)
         << names[i]
         << resetiosflags(ios::left)
         << setw(10)
         << setprecision(1)
         << values[i]
         << endl;
```

Program vytiskne tento seznam:

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

Chcete-li odstranit vědecký zápis, vložte tento příkaz před **pro** smyčka:

```cpp
cout << setiosflags(ios::fixed);
```

S pevnou zápisu program vytiskne se jedna číslice za desetinnou čárkou.

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

Pokud změníte `ios::fixed` příznak, který `ios::scientific`, program zobrazí toto:

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

Program znovu, vytiskne jednu číslici za desetinnou čárkou. Pokud `ios::fixed` nebo `ios::scientific` je nastaven, hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud ani příznak nastaven, hodnota přesnosti určuje celkový počet platných číslic. `resetiosflags` Manipulátor vymaže tyto příznaky.

## <a name="vclrfradixanchor6"></a> Radix

`dec`, `oct`, A `hex` manipulátory nastavit výchozí základ pro vstup a výstup. Například, pokud je vložit `hex` manipulátor do výstupního datového proudu objekt správně přeloží reprezentaci vnitřního dat celých čísel do šestnáctkové výstupní formát. Jsou čísla zobrazena pomocí číslic a až f v malá písmena v případě [velká](../standard-library/ios-functions.md#uppercase) příznak je vymazat (výchozí); v opačném případě se zobrazí velkými písmeny. Výchozí základ číselné soustavy je `dec` (decimal).

## <a name="quoted-strings-c14"></a>Řetězce v uvozovkách (C ++ 14)

Když řetězec vložíte do datového proudu, můžete snadno načíst stejný řetězec zpět voláním členské funkce stringstream::str(). Nicméně, pokud chcete použít operátor extrakce k vložení datový proud do nového řetězce později, může získáte neočekávaný výsledek protože >> operátor ve výchozím nastavení se zastaví, jakmile nalezne první prázdným znakem.

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

Toto chování je možné překonat ručně, ale aby verzemi řetězec pohodlnější, C ++ 14 přidá `std::quoted` manipulátor v datový proud stream \<iomanip >. Při vložení `quoted()` obklopuje řetězci s oddělovačem (dvojité uvozovky "" "ve výchozím nastavení) a při extrakci zpracovává datový proud se mají extrahovat všechny znaky až do konečného oddělovač. Žádné vložené uvozovky jsou uvozeny řídicími znaky s řídicím znakem ("\\\\' ve výchozím nastavení).

Oddělovače jsou k dispozici pouze v objektu datového proudu. nejsou k dispozici v extrahovaných řetězců, ale jsou k dispozici v řetězec vrácený funkcí [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str).

Prázdné znaky chování operace vložení a extrakci nezávisí jak řetězec je reprezentován v kódu, tak je užitečné bez ohledu na to, jestli je vstupní řetězec literálu nezpracovaného řetězce nebo regulárního řetězec v uvozovkách operátor. Vstupní řetězec, ať formátem, lze mít vkládat uvozovky, konce řádků, karty a podobně a všechny tyto se zachovají quoted() manipulátor.

Další informace a příklady celý kód, naleznete v tématu [v uvozovkách](../standard-library/iomanip-functions.md#quoted).

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
