---
title: "Standardní převody | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 954ba431378317a3f9079677f49223a336af5d9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="standard-conversions"></a>Standardní převody
Jazyk C++ definuje převody mezi základními typy. Definuje také převody pro ukazatel, odkaz a pro odvozené typy ukazatele na člena. Tyto převody jsou označovány jako „standardní převody“. (Další informace o odvozené typy, typy a standardní typy najdete v tématu [typy](http://msdn.microsoft.com/en-us/6882ee83-ea32-4373-8d57-c3efbbc15af0).)  
  
 Tato část popisuje následující standardní převody:  
  
-   Integrální povýšení  
  
-   Integrální převody  
  
-   Převody s plovoucí desetinnou čárkou  
  
-   Převody s plovoucí desetinnou čárkou a integrální převody  
  
-   Aritmetické převody  
  
-   Převody ukazatele  
  
-   Převody odkazů  
  
-   Převody ukazatele na člena  
  
    > [!NOTE]
    >  Uživatelské typy mohou zadat své vlastní převody. Převod uživatelem definované typy je popsaná v [konstruktory](../cpp/constructors-cpp.md) a [převody](../cpp/user-defined-type-conversions-cpp.md).  
  
 Následující kód provede převody (v tomto příkladu integrální povýšení):  
  
```  
long  long_num1, long_num2;  
int   int_num;  
  
// int_num promoted to type long prior to assignment.  
long_num1 = int_num;  
  
// int_num promoted to type long prior to multiplication.  
long_num2 = int_num * long_num2;  
```  
  
 Výsledkem převodu je l-hodnota pouze v případě, že vytvoří typ odkazu. Například uživatelem definovaný převod deklarován jako `operator int&()` vrátí odkaz a je l hodnota. Ale převodu z deklarován jako `operator int()`vrátí objekt a není l hodnota.  
  
## <a name="integral-promotions"></a>Integrální povýšení  
 Objekty celočíselného typu lze převést na jiné širší celočíselné typy (to znamená na typy, které mohou představovat větší množinu hodnot). Tento typ rozšiřujícího převodu se nazývá „povýšení celočíselného typu“. S povýšením celočíselného typu lze všude ve výrazu, kde lze použít jiný celočíselný typ, použít následující:  
  
-   Objekty, literály a konstanty typu `char` a `short int`  
  
-   Výčtové typy  
  
-   Bitová pole typu `int`  
  
-   Výčty  
  
 Povýšení typu v jazyce C++ „zachovávají hodnotu“. To znamená, že hodnota po povýšení zůstane stejná jako hodnota před povýšením. U povýšení typu zachovávajícího hodnotu jsou objekty kratších celočíselných typů (například bitová pole nebo objekty typu `char`) povýšeny na typ `int`, pokud může typ `int` v plném rozsahu reprezentovat původní typ. Pokud typ `int` nemůže reprezentovat úplný rozsah hodnot, je objekt povýšen na typ `unsigned int`. Ačkoli je tato strategie stejná jako ve standardu ANSI C, převody zachovávající hodnotu nezachovávají to, zda objekt má nebo nemá znaménko.  
  
 Povýšení typu zachovávající hodnotu a povýšení typu, která normálně zachovávají znaménko, vrátí stejné výsledky. Mohou však vrátit různé výsledky, pokud je povýšený typ objektu jedním z následujících:  
  
-   Operand z  **/** , `%`, `/=`, `%=`,  **<** ,  **\< =** ,  **>** , nebo**>=**  
  
     Tyto operátory spoléhají pro stanovení výsledku na znaménko. Proto povýšení typu zachovávající hodnotu a povýšení typu zachovávající znaménko vrátí při použití s těmito operandy různé výsledky.  
  
-   Levý operand  **>>**  nebo**>>=**  
  
     Tyto operátory zacházejí při provádění operací posunu s hodnotami se znaménkem nebo bez znaménka odlišně. U hodnot se znaménkem posunutí hodnoty vpravo způsobí, že je bit znaménka posunut na pozici uvolněného bitu. U hodnot bez znaménka jsou pozice uvolněných bitů vyplněny nulami.  
  
-   Argument přetížené funkce nebo operand přetíženého operátoru, který závisí na tom, zda je typ tohoto operandu pro párování argumentů se znaménkem nebo bez. (Viz [přetížený operátory](../cpp/operator-overloading.md) Další informace o definování přetížené operátory.)  
  
## <a name="integral-conversions"></a>Integrální převody  
 Mezi celočíselnými typy jsou prováděny celočíselné převody. Integrální typy jsou `char`, `int`, a **dlouho** (a **krátké**, **podepsané**, a `unsigned` verze těchto typů).  
  
 **Podepsaného na nepodepsané**  
  
 Objekty celočíselných typů se znaménkem lze převést na odpovídající typy bez znaménka. Když tyto převody nastanou, skutečný bitový vzor se nezmění. Změní se však interpretace dat. Vezměte v úvahu tento kód:  
  
```  
  
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
  
 V předchozím příkladu je proměnná `signed short` typu `i` definována a inicializována na záporné číslo. Výraz `(u = i)` způsobí, že `i` má být převeden na **nepodepsané prostě** před přiřazení `u`.  
  
 **Unsigned na signed**  
  
 Objekty celočíselných typů bez znaménka lze převést na odpovídající typy se znaménkem. Avšak takový převod může způsobit špatné vyhodnocení dat, je-li hodnota objektu bez znaménka mimo rozsah reprezentovatelný typem se znaménkem, jak je uvedeno v následujícím příkladu:  
  
```  
  
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
  
 V předchozím příkladu `u` je `unsigned` **krátké** integrální objekt, který musí být převedena na podepsané množství při vyhodnocování výrazu `(i = u)`. Vzhledem k tomu, že jeho hodnotu nelze vyjádřit správně pomocí typu `signed short`, jsou data chybně interpretována, jak je znázorněno.  
  
## <a name="floating-point-conversions"></a>Plovoucí převody bodu  
 Objekt typu s plovoucí desetinnou čárkou lze bezpečně převést na přesnější typ s plovoucí desetinnou čárkou, to znamená, že převod nezpůsobí ztrátu významu. Například převody z **float** k **dvojité** nebo z **dvojité** k `long double` jsou bezpečné a hodnota se nemění.  
  
 Objekt typu s plovoucí desetinnou čárkou lze převést na méně přesný typ, pokud je v rozsahu vyjádřitelném tímto typem. (Viz [plovoucí omezení](../cpp/floating-limits.md) pro rozsahy typů s plovoucí čárkou.) Pokud nelze původní hodnotu přesně vyjádřit, může být převedena buď na další vyšší, nebo na další nižší vyjádřitelnou hodnotu. Pokud žádná taková hodnota neexistuje, výsledek není definován. Podívejte se na následující příklad:  
  
```  
cout << (float)1E300 << endl;  
```  
  
 Maximální hodnota reprezentovat podle typu **float** je 3.402823466E38 – mnohem nižší hodnotu než 1E300. Proto je číslo převedeno na nekonečno a výsledek je 1.#INF.  
  
## <a name="conversions-between-integral-and-floating-point-types"></a>Převody mezi bodu plovoucí a integrální typy  
 Určité výrazy mohou způsobit převod objektů typu s plovoucí desetinnou čárkou na celočíselné typy nebo naopak. Jakmile je objekt celočíselného typu převeden na typ s plovoucí desetinnou čárkou a původní hodnotu nelze převést zcela přesně, výsledkem je nejbližší vyšší nebo nejbližší nižší reprezentovatelná hodnota.  
  
 Při převodu objektu typu s plovoucí desetinnou čárkou na celočíselný typ je desetinná část zkrácena. V procesu převodu se neuskuteční zaokrouhlení. Zkrácení znamená, že číslo jako 1.3 jsou převedeny na 1 a-1.3 je převést na hodnotu -1.  
  
## <a name="arithmetic-conversions"></a>Aritmetické převody  
 Mnoho binární operátory (popsané v [výrazy s binárními operátory](../cpp/expressions-with-binary-operators.md)) způsobit, že převody operandy a poskytují výsledky stejným způsobem. Způsob, jakým tyto operátory provádějí převody, se nazývá „obvyklé aritmetické převody“. Aritmetické převody operandů různých nativních typů jsou prováděny tak, jak je znázorněno v následující tabulce. Typy typedef se chovají podle svých základních nativních typů.  
  
### <a name="conditions-for-type-conversion"></a>Podmínky pro převod typu  
  
|Splněné podmínky|Převod|  
|--------------------|----------------|  
|Buď operand je typu **long double**.|Další operand je převést na typ **long double**.|  
|Předcházející podmínku nebyly splněny a buď operand je typu **dvojité**.|Další operand je převést na typ **dvojité**.|  
|Předcházející podmínky nebyly splněny a buď operand je typu **float**.|Další operand je převést na typ **float**.|  
|Předcházející podmínky nebyly splněny (žádný z operandů není typ s plovoucí desetinnou čárkou).|Celočíselné povýšení je s těmito operandy provedeno následovně:<br /><br /> – Pokud je buď operand typu `unsigned` **dlouho**, jiné operand je převést na typ `unsigned long`.<br />– Pokud předcházející podmínky nejsou splněné, a pokud je buď operand typu **dlouho** a dalších typu `unsigned` `int`, oba operandy se převedou na typ `unsigned long`.<br />– Pokud předchozí dvě podmínky nejsou splněné, a pokud je buď operand typu **dlouho**, jiné operand je převést na typ **dlouho**.<br />– Pokud nejsou splněné výše uvedených tří podmínek, a pokud je buď operand typu `unsigned int`, jiné operand je převést na typ `unsigned int`.<br />– Pokud žádná z výše uvedených podmínek jsou splněny, jsou oba operandy převést na typ `int`.|  
  
 Následující kód znázorňuje pravidla převodu, která jsou popsána v tabulce:  
  
```  
  
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
  
 První příkaz v předchozím příkladu znázorňuje násobení dvou celočíselných typů, `iVal` a `ulVal`. Podmínka je splněna, pokud ani jeden operand není typu s plovoucí desetinnou čárkou a jeden operand je typu `unsigned int`. Proto je druhý operand, `iVal`, převeden na typ `unsigned int`. Výsledek je přiřazen do proměnné `dVal`. Podmínka splněná je, že jeden operand je typu **dvojité**; proto `unsigned int` výsledkem násobení je převést na typ **dvojité**.  
  
 Druhý příkaz v předchozím příkladu zobrazuje přidání **float** a typ integrální `fVal` a `ulVal`. `ulVal` Proměnné je převést na typ **float** (třetí podmínka v tabulce). Výsledkem přidání je převést na typ **dvojité** (druhá podmínky v tabulce) a přiřazení `dVal`.  
  
## <a name="pointer-conversions"></a>Převody ukazatele  
 Ukazatele lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech.  
  
### <a name="pointer-to-classes"></a>Ukazatel na třídy  
 Jsou dva případy, ve kterých ukazatel na třídu lze převést na ukazatel na základní třídu.  
  
 Prvním případě je, pokud zadaná základní třída je přístupný a převod je jednoznačné. (Viz [vícenásobné třídy Base](../cpp/multiple-base-classes.md) Další informace o nejednoznačný odkazy na základní třídy.)  
  
 Zda je přístupný základní třídu závisí na druhu dědičnosti použít v odvození. Vezměte v úvahu dědičnosti zobrazené na následujícím obrázku.  
  
 ![Dědičnost graf zobrazující základní & č. 45; usnadnění třída](../cpp/media/vc38xa1.gif "vc38XA1")  
Graf dědičnosti pro obrázek usnadnění základní třídy  
  
 V následující tabulce jsou uvedeny základní třídy usnadnění pro situaci zobrazené na obrázku.  
  
### <a name="base-class-accessibility"></a>Základní třída pro usnadnění přístupu  
  
|Typ funkce|Odvození|Převod z<br /><br /> B * k A\* právní?|  
|----------------------|----------------|-------------------------------------------|  
|Externí funkce (není třída obor)|Soukromé|Ne|  
||Chráněno|Ne|  
||Public|Ano|  
|B – členská funkce (v oboru B)|Soukromé|Ano|  
||Chráněno|Ano|  
||Public|Ano|  
|C – členská funkce (v oboru C)|Soukromé|Ne|  
||Chráněno|Ano|  
||Public|Ano|  
  
 Ve kterém ukazatel na třídu lze převést na ukazatel na základní třídu druhém případě je při použití explicitní převod typu. (Viz [výrazy s explicitní převody typu](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Další informace o explicitní převody typu.)  
  
 Výsledek takový převod je ukazatel "určitých podřízených objektů," část objektu, který je zcela popsaný v základní třídě.  
  
 Následující kód definuje dvě třídy `A` a `B`, kde `B` je odvozený od `A`. (Další informace o dědičnosti najdete v tématu [odvozené třídy](../cpp/inheritance-cpp.md).) Potom definuje `bObject`, objekt typu `B`a dva ukazatele (`pA` a `pB`), přejděte na objekt.  
  
```  
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
  
 Ukazatele `pA` je typu `A *`, která jde interpretovat jako význam "ukazatel na objekt typu `A`." Členové `bObject` `(`například `BComponent` a `BMemberFunc`) jsou jedinečné pro typ `B` a jsou proto nedostupné prostřednictvím `pA`. `pA` Ukazatel umožňuje přístup pouze na tyto charakteristiky (členské funkce a data) objektu, které jsou definovány v třídě `A`.  
  
### <a name="pointer-to-function"></a>Ukazatel na funkci  
 Ukazatel na funkci můžete převést na typ **void \*** , pokud typ **void \***  je dostatečně velký pro uložení tohoto ukazatele.  
  
### <a name="pointer-to-void"></a>Ukazatel na void  
 Ukazatele na typ `void` lze převést na ukazatele na jiný typ, avšak pouze pomocí přetypování explicitního typu (na rozdíl od jazyka C). (Viz [výrazy s explicitní převody typu](http://msdn.microsoft.com/en-us/060ad6b4-9592-4f3e-8509-a20ac84a85ae) Další informace o typu přetypování.) Ukazatel na jakýkoli typ může být implicitně převedena na ukazatel na typ `void`. Ukazatel na objekt neúplné typu lze převést na ukazatel na `void` (implicitně) a zpět (explicitně). Výsledek takového převodu je roven hodnotě původního ukazatele. Objekt je považován za neúplný, pokud je deklarovaný, ale není k dispozici dostatek informací, na základě kterých lze určit jeho velikost nebo základní třídu.  
  
 Ukazatel na libovolný objekt, který není **const** nebo `volatile` může být implicitně převedena na ukazatel typu **void \*** .  
  
### <a name="const-and-volatile-pointers"></a>ukazatelé const a volatile  
 C++ neposkytuje standardní převod z **const** nebo `volatile` typu typ, který není **const** nebo `volatile`. Libovolné druhy převodu lze však určit pomocí přetypování explicitních typů (včetně převodů, které nejsou bezpečné).  
  
> [!NOTE]
>  Ukazatele na členy jazyka C++, s výjimkou ukazatelů na statické členy, jsou odlišné od běžných ukazatelů a nemají stejné standardní převody. Ukazatele na statické členy jsou normální ukazatele a mají stejné převody jako normální ukazatele.   
  
### <a name="null-pointer-conversions"></a>převody ukazatele Null.  
 Celočíselné konstantní výraz, který se vyhodnotí na hodnotu nula, nebo takové výrazu přetypovat na typ ukazatele jsou převedeny na ukazatel názvem "nulového ukazatele." Tento ukazatel zaručuje nerovnost při porovnání s ukazatelem na libovolný platný objekt nebo funkci (kromě ukazatelů na objekty se základem, které mohou mít stejný posun a stále ukazovat na různé objekty).  
  
 V C ++ 11 [nullptr](../cpp/nullptr.md) typ musí být upřednostňované na ukazatele null stylu jazyka C.  
  
### <a name="pointer-expression-conversions"></a>Převody ukazatele výraz  
 Každý výraz typu pole lze převést na ukazatel stejného typu. Výsledkem převodu je ukazatel na první prvek pole. Následující příklad ukazuje takový převod:  
  
```  
char szPath[_MAX_PATH]; // Array of type char.  
char *pszPath = szPath; // Equals &szPath[0].  
```  
  
 Výraz, jehož výsledkem je funkce vracející určitý typ, je převeden na ukazatel na funkci vracející tento typ kromě těchto případů:  
  
-   Výraz je použít jako operand operátoru adresy (**&**).  
  
-   Výraz je použit jako operand operátoru volání funkce.  
  
## <a name="reference-conversions"></a>Převody odkazů  
 Odkaz na třídu lze převést na odkaz na základní třídu v následujících případech:  
  
-   Zadaná základní třída je dostupné.  
  
-   Převod je jednoznačný. (Viz [vícenásobné třídy Base](../cpp/multiple-base-classes.md) Další informace o nejednoznačný odkazy na základní třídy.)  
  
 Výsledkem převodu je ukazatel na podobjekt, který představuje základní třídu.  
  
## <a name="pointer-to-member"></a>Ukazatel na člena  
 Ukazatele na členy třídy lze převádět během přiřazení, inicializace, porovnání a v jiných výrazech. Tato část popisuje následující převody ukazatele na člen:  
  
## <a name="pointer-to-base-class-member"></a>Ukazatel na člena třídy base  
 Ukazatel na člen základní třídy lze převést na ukazatel na člen třídy z ní odvozené, pokud jsou splněny následující podmínky:  
  
-   Inverzní převod z ukazatele na odvozenou třídu na ukazatel na základní třídu je přístupný.  
  
-   Odvozená třída virtuálně nedědí ze základní třídy.  
  
 Je-li levý operand ukazatel na člen, pravý operand musí být typu ukazatele na člen nebo konstantní výraz, který je vyhodnocen na hodnotu 0. Toto přiřazení je platné pouze v následujících případech:  
  
-   Pravý operand je ukazatel na člen stejné třídy jako levý operand.  
  
-   Levý operand je ukazatel na člen třídy odvozené veřejně a jednoznačně z třídy pravého operandu.  
  
## <a name="integral-constant-conversions"></a>Integrální konverze konstant  
 Celočíselný konstantní výraz, který je vyhodnocen na hodnotu nula, je převeden na ukazatel zvaný „nulový ukazatel“. Tento ukazatel zaručuje nerovnost při porovnání s ukazatelem na libovolný platný objekt nebo funkci (kromě ukazatelů na objekty se základem, které mohou mít stejný posun a stále ukazovat na různé objekty).  
  
 Následující kód znázorňuje definici ukazatele na člen `i` třídy `A`. Ukazatel `pai` je inicializován na hodnotu 0, což je nulový ukazatel.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka jazyka C++](../cpp/cpp-language-reference.md)