---
title: Používání operátorů insertion a řízení formátu
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 2cf399501c0eab32e8bee80dfcb98d870c0193cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458029"
---
# <a name="using-insertion-operators-and-controlling-format"></a>Používání operátorů insertion a řízení formátu

Toto téma ukazuje, jak ovládat formátování a jak vytvořit operátory vkládání pro vlastní třídy. Operátor vložení ( **<<** ), který je přednaprogramován pro všechny standardní C++ datové typy, odesílá bajty do objektu výstupního datového proudu. Operátory vkládání fungují s předdefinovanými "manipulacemi", které jsou prvky, které mění výchozí formát celočíselných argumentů.

Formát můžete řídit pomocí následujících možností:

- [Šířka výstupu](#vclrfoutputwidthanchor3)

- [Bod](#vclrfalignmentanchor4)

- [Číslic](#vclrfprecisionanchor5)

- [Radix](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a>Šířka výstupu

Pro zarovnávání výstupu zadáte šířku výstupu pro každou položku tak, že `setw` umístíte manipulátor do datového proudu nebo `width` zavoláte členskou funkci. V tomto příkladu se vpravo zarovnají hodnoty ve sloupci, které mají aspoň 10 znaků v šířce:

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

Úvodní prázdné znaky jsou přidány do libovolné hodnoty menší než 10 znaků.

Chcete-li doplnit pole, použijte `fill` členskou funkci, která nastaví hodnotu ohraničujícího znaku pro pole, která mají zadanou šířku. Výchozí hodnota je prázdná. Chcete-li odblokovat sloupec čísel pomocí hvězdiček, upravte předchozí smyčku **for** následujícím způsobem:

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

Manipulátor nahrazuje znak nového řádku (`'\n'`). `endl` Výstup bude vypadat nějak takto:

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

K určení šířky datových prvků na stejném řádku použijte `setw` manipulátor:

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

Členská funkce je deklarována \<v iostream – >. `width` Pokud používáte \<nebo jakékoli jiné manipulátor s argumenty, musíte zahrnout iomanip >. `setw` Ve výstupu jsou řetězce vytištěny v poli šířky 6 a celá čísla v poli šířky 10:

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

`setw` Ani ani nezkrátíhodnoty`width` . Pokud formátovaný výstup přesahuje šířku, vytiskne se celá hodnota v závislosti na nastavení přesnosti datového proudu. `setw` A`width` mají vliv pouze na následující pole. Šířka pole se vrátí k výchozímu chování (potřebná šířka) po vytištění jednoho pole. Ostatní možnosti formátu datového proudu ale zůstanou v platnosti, dokud se nezmění.

## <a name="vclrfalignmentanchor4"></a>Bod

Výstupní datové proudy jsou standardně zarovnané na text vpravo. Pokud chcete názvy v předchozím příkladu Zarovnat doleva a zarovnat je vpravo, nahraďte smyčku **for** následujícím způsobem:

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

Výstup bude vypadat nějak takto:

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

Příznak levého zarovnání se nastaví pomocí [setiosflags](../standard-library/iomanip-functions.md#setiosflags) manipulátor s `left` enumerátorem. Tento enumerátor je definovaný ve třídě [iOS](../standard-library/basic-ios-class.md) , takže jeho reference musí zahrnovat předponu **iOS::** . [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) manipulátor vypne příznak vlevo. Na rozdíl `width` od `setw`a, efekt `setiosflags` a `resetiosflags` je trvalý.

## <a name="vclrfprecisionanchor5"></a>Číslic

Výchozí hodnota pro přesnost s plovoucí desetinnou čárkou je šest. Například číslo 3466,9768 se vytiskne jako 3466,98. Chcete-li změnit způsob, jakým se tato hodnota tiskne, použijte [setprecision](../standard-library/iomanip-functions.md#setprecision) manipulátor. Manipulátor má dva příznaky: [fixed](../standard-library/ios-functions.md#fixed) a [vědecký](../standard-library/ios-functions.md#scientific). Pokud je nastavená hodnota [pevná](../standard-library/ios-functions.md#fixed) , číslo se vytiskne jako 3466,976800. Pokud `scientific` je nastavena, bude vytištěna jako 3.4669773 + 003.

Chcete-li zobrazit čísla s plovoucí desetinnou čárkou, která jsou uvedena v [Zarovnání](#vclrfalignmentanchor4) s jednou platnou číslicí, nahraďte smyčku **for** následujícím způsobem:

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

Chcete-li odstranit vědecký zápis, vložte tento příkaz před smyčku **for** :

```cpp
cout << setiosflags(ios::fixed);
```

S pevným zápisem program tiskne za desetinnou čárkou jednu číslici.

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

Pokud `ios::fixed` příznak změníte na, program `ios::scientific`ho vytiskne:

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

Program znovu vytiskne jednu číslici za desetinnou čárkou. Pokud je nastavená `ios::scientific`nebo, hodnota přesnosti určuje počet číslic za desetinnou čárkou. `ios::fixed` Pokud není nastaven žádný příznak, hodnota přesnosti určí celkový počet platných číslic. `resetiosflags` Manipulátor tyto příznaky vymaže.

## <a name="vclrfradixanchor6"></a> Radix

Manipulace s `oct` ,a`hex` nastavují výchozí základ pro vstup a výstup. `dec` Například pokud vložíte `hex` manipulátor do výstupního datového proudu, objekt správně přeloží interní reprezentace celých čísel do hexadecimálního formátu. Čísla se zobrazí s číslicemi a až f v malých případech, pokud je příznak [velkými](../standard-library/ios-functions.md#uppercase) písmeny jasný (výchozí). v opačném případě se zobrazí v horním případě. Výchozí základ číselné soustavy `dec` je (desítková).

## <a name="quoted-strings-c14"></a>Řetězce v uvozovkách (C++ 14)

Když vložíte řetězec do datového proudu, můžete snadno načíst stejný řetězec zpět voláním členské funkce stringstream:: str (). Pokud však chcete použít operátor extrakce pro vložení datového proudu do nového řetězce později, může dojít k neočekávanému výsledku, protože > operátor > ve výchozím nastavení zastaví, když nalezne první prázdný znak.

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

Toto chování se dá překonat ručně, ale pokud chcete, aby se Trip řetězec, c++ 14 přidá `std::quoted` manipulátor Stream do \<iomanip >. Po vložení `quoted()` ohraničuje řetězec pomocí oddělovače (ve výchozím nastavení dvojité uvozovky) a po extrakci zpracovává všechny znaky, dokud není nalezen konečný oddělovač. Všechny vložené uvozovky jsou uvozeny řídicím znakem (\\\\ve výchozím nastavení).

Oddělovače jsou k dispozici pouze v objektu Stream; nejsou přítomny v extrahovaném řetězci, ale jsou přítomny v řetězci vráceném funkcí [basic_stringstream:: str](../standard-library/basic-stringstream-class.md#str).

Chování prázdných znaků při vkládání a extrakci je nezávislé na způsobu reprezentace řetězce v kódu, takže operátor v uvozovkách je užitečný bez ohledu na to, zda je vstupní řetězec nezpracovaným řetězcovým literálem nebo regulárním řetězcem. Vstupní řetězec bez ohledu na formát může mít vložené uvozovky, zalomení řádků, tabulátory atd. a všechny tyto řetězce budou zachovány v uvozovkách () manipulátor.

Další informace a příklady úplných kódů naleznete v [uvozovkách](../standard-library/iomanip-functions.md#quoted).

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)
