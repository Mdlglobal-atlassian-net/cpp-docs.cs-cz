---
title: "Používání operátorů Insertion a řízení formátu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2794da411458ccdf83725b80a6b5ba8371e53248
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="using-insertion-operators-and-controlling-format"></a>Používání operátorů insertion a řízení formátu
Toto téma ukazuje, jak řídit formát a postup vytvoření operátorů insertion pro vaše vlastní třídy. Vložení (**<<**) operátor, který je naprogramovaných, pro všechny standardní datové typy C++, odešle do výstupního datového proudu objekt bajtů. Operátorů insertion pracovat předdefinované "manipulátory,", které jsou elementy, které Změna výchozího formátu argumentů celé číslo.  
  
 Můžete řídit formát s následující možnosti:  
  
- [Šířka výstupu](#vclrfoutputwidthanchor3)  
  
- [Zarovnání](#vclrfalignmentanchor4)  
  
- [Přesnost](#vclrfprecisionanchor5)  
  
- [Radix](#vclrfradixanchor6)  
  
##  <a name="vclrfoutputwidthanchor3"></a>Šířka výstupu  
 Chcete-li zarovnat výstup, zadejte šířku výstup pro každou položku tím, že `setw` manipulator v datovém proudu nebo voláním **šířka** – členská funkce. Tento příklad vpravo zarovná hodnoty ve sloupci minimálně 10 znaků, který je široké:  
  
```  
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
  
### <a name="output"></a>Výstup  
  
```  
    1.23 
    35.36 
    653.7 
4358.24  
```  
  
 Úvodní prázdné hodnoty se přidají na jakoukoli hodnotu široké méně než 10 znaků.  
  
 K vyplnění pole, použijte **výplně** členská funkce, která nastaví hodnota odsazení znaku pro pole, které mají nastavená šířka. Výchozí hodnota je prázdné. K vyplnění sloupci čísel pomocí hvězdiček, upravte předchozí **pro** cykly následujícím způsobem:  
  
```  
for(int i = 0; i <4; i++)  
{  
    cout.width(10);

 cout.fill('*');

    cout <<values[i] <<endl;  
}  
```  
  
 `endl` Manipulator nahradí znak nového řádku (`'\n'`). Výstup vypadá takto:  
  
```  
******1.23  
*****35.36  
*****653.7  
***4358.24  
```  
  
 Pokud chcete zadat šířky pro datové prvky ve stejném řádku, použijte `setw` manipulator:  
  
```  
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
      cout << setw( 6 )  << names[i]  
           << setw( 10 ) << values[i] << endl;  
}  
```  
  
### <a name="output"></a>Výstup  
 **Šířka** v deklaraci funkce člen \<iostream >. Pokud používáte `setw` nebo jakékoli jiné manipulator s argumenty, je nutné zahrnout \<iomanip – >. Ve výstupu jsou řetězce vytištěn v pole šířky 6 a celá čísla v poli šířky 10:  
  
```  
    Zoot 1.23  
Jimmy     35.36  
    Al 653.7  
    Stan 4358.24  
```  
  
 Ani `setw` ani **šířka** zkrátí hodnoty. Pokud výstup ve formátu překračuje šířku celou hodnotu vytiskne, podstoupí nastavení přesnost datového proudu. Obě `setw` a **šířka** ovlivňují jenom následující pole. Šířka pole se vrátí do jeho výchozí chování (nezbytná šířka) po vytištění jedno pole. Ale jiné možnosti formátu datového proudu zůstávají platná, dokud změnit.  
  
##  <a name="vclrfalignmentanchor4"></a>Zarovnání  
 Výstupní datové proudy výchozí nastavení text zarovnaný doprava. Názvy v předchozím příkladu zarovnání doleva a doprava align čísla, nahraďte **pro** cykly následujícím způsobem:  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)  <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10) <<values[i] <<endl;  
```  
  
 Výstup vypadá takto:  
  
```  
Zoot        1.23  
Jimmy      35.36  
Al         653.7  
Stan     4358.24  
```  
  
 Příznak left-align je nastaven pomocí [setiosflags](../standard-library/iomanip-functions.md#setiosflags) manipulator s `left` enumerátor. Tento výčet je definován v [ios](../standard-library/basic-ios-class.md) třídy, takže musí obsahovat odkaz na jeho **ios::** předponu. [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) manipulator Vypne příznak left-align. Na rozdíl od **šířka** a `setw`, účinek `setiosflags` a `resetiosflags` je trvalá.  
  
##  <a name="vclrfprecisionanchor5"></a>Přesnost  
 Výchozí hodnota s plovoucí desetinnou čárkou přesnost je šest. Například číslo 3466.9768 vytiskne jako 3466.98. Můžete změnit způsob, jakým vytiskne tato hodnota [setprecision](../standard-library/iomanip-functions.md#setprecision) manipulator. Manipulator má dva příznaky: [pevné](../standard-library/ios-functions.md#fixed) a [scientific](../standard-library/ios-functions.md#scientific). Pokud [pevné](../standard-library/ios-functions.md#fixed) nastavena, číslo výtisků jako 3466.976800. Pokud **scientific** není nastaven, vytiskne jako 3.4669773 + 003.  
  
 Chcete-li zobrazit čísla s plovoucí desetinnou čárkou, která se zobrazují v [zarovnání](#vclrfalignmentanchor4) nahradil jednu číslici, **pro** cykly následujícím způsobem:  
  
```  
for (int i = 0; i <4; i++)  
    cout <<setiosflags(ios::left)  
 <<setw(6)    
 <<names[i]  
 <<resetiosflags(ios::left)  
 <<setw(10)   
 <<setprecision(1)  
 <<values[i]   
 <<endl;  
```  
  
 Program vytiskne tohoto seznamu:  
  
```  
Zoot          1  
Jimmy     4e+001  
Al        7e+002  
Stan      4e+003  
```  
  
 K vyloučení exponenciální notace, vložte tento příkaz před **pro** smyčka:  
  
```  
cout <<setiosflags(ios::fixed);
```  
  
 S pevnou zápis program vytiskne s jedna číslice za desetinnou čárkou.  
  
```  
Zoot         1.2  
Jimmy       35.4  
Al         653.7  
Stan      4358.2  
```  
  
 Pokud změníte **ios::fixed** příznak, který **ios::scientific**, program zobrazí toto:  
  
```  
Zoot    1.2e+000  
Jimmy   3.5e+001  
Al      6.5e+002  
Stan    4.4e+003  
```  
  
 Program znovu, vytiskne jedna číslice za desetinnou čárkou. Pokud má jedna **ios::fixed** nebo **ios::scientific** není nastaven, hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud ani příznak nastaven, hodnota přesnosti určuje celkový počet platných číslic. `resetiosflags` Manipulator vymaže tyto příznaky.  
  
##  <a name="vclrfradixanchor6"></a> Radix  
 **Dec**, **oct**, a **šestnáctkových** manipulátory nastavit základ – výchozí pro vstup a výstup. Například, pokud je vložit **šestnáctkových** manipulator do výstupního datového proudu objekt správně překládá reprezentace interních datových celých čísel do formátu hexadecimální výstup. Jsou čísla zobrazí pomocí číslic a až f v malá Pokud [velká](../standard-library/ios-functions.md#uppercase) příznak je clear (výchozí); jinak, jsou zobrazeny velkými písmeny. Základ – výchozí je **dec** (decimal).  
  
## <a name="quoted-strings-c14"></a>Uvozovkách řetězce (C ++ 14)  
 Pokud řetězec vložíte do datového proudu, můžete snadno načíst do jednoho řetězce zpět voláním členské funkce stringstream::str(). Ale pokud chcete použít operátor extrakce pro vložení do datového proudu do nového řetězce později, může se zobrazit neočekávaný výsledek protože >> operátor ve výchozím nastavení se zastaví, pokud se setká s první prázdný znak.  
  
```  
 
std::stringstream ss;  
std::string inserted = "This is a sentence.";  
std::string extracted;  
 
ss <<inserted;  
ss>> extracted;  
 
std::cout <<inserted;     //  This is a sentence.  
std::cout <<extracted;   //   This  
```  
  
 Toto chování lze překonat ručně, ale aby odezvy řetězec pohodlnější, C ++ 14 přidá `std::quoted` stream manipulator v `<iomanip>`. Při vložení `quoted()` obklopuje řetězec s oddělovačem (dvojitých uvozovek ' "' ve výchozím nastavení) a při extrakci zpracovává datový proud extrahujte všechny znaky až do konečného oddělovač. Jsou uvozeny uvozovacím znakem žádné embedded uvozovky s řídicí znak ('\\\\se ve výchozím nastavení).  
  
 Oddělovače jsou k dispozici pouze v objektu datového proudu. se nenachází v extrahované řetězec, ale jsou přítomna v řetězec vrácený [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str).  
  
 Prázdné znaky chování operací vložení a extrakce je nezávisle na tom, jak je řetězec reprezentována v kódu tak uvozovkách operátor je užitečné, bez ohledu na to, jestli vstupní řetězec je nezpracované řetězcový literál nebo řetězec regulárního. Vstupní řetězec, ať formát, můžete s vloženými uvozovky, zalomení řádků, karty a podobně a všechny tyto se zachovají quoted() manipulator.  
  
 Další informace a příklady úplného kódu najdete v tématu [v uvozovkách](../standard-library/iomanip-functions.md#quoted).  
  
## <a name="see-also"></a>Viz také  
 [Výstupní streamy](../standard-library/output-streams.md)   

