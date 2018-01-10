---
title: "Přehled deklarátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 18a3f12ac87f0165c74aaa487913f679f1a9941e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-declarators"></a>Přehled deklarátorů
Deklarátory jsou ty součásti deklarace, které určují názvy objektů a funkcí. Určují také, zda je pojmenovaný objekt objektem, ukazatelem, referencí nebo polem.  Ačkoli deklarátory neurčují základní typ, upravují informace o typu v základním typu a určují tak odvozené typy jako ukazatele, reference a pole.  Deklarátor použitý ve funkci spolupracuje se specifikátorem typu na plném určení návratového typu funkce jako objekt, ukazatel nebo reference. (Specifikátory, popsané v [deklarace a definice](declarations-and-definitions-cpp.md), nesou vlastnosti, například třída typ a úložiště. Modifikátory, popsané v této části a v [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md), upravte deklarátory.) Následující obrázek ukazuje kompletní deklaraci funkce `MyFunction` a označuje komponenty deklarace.  
  
 ![Modifikátory specifikátory a deklarátory](../cpp/media/vc38qy1.gif "vc38QY1")  
Specifikátory, modifikátory a deklarátory  
  
 **Konkrétní Microsoft**  
  
 Většinu klíčových slov rozšířených společností Microsoft lze použít jako modifikátory a vytvořit tak odvozené typy. Nejsou to specifikátory ani deklarátory. (Viz [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).)  
  
 **Konkrétní Microsoft END**  
  
 Deklarátory se vyskytují v syntaxi deklarace za nepovinným seznamem specifikátorů. Tyto specifikátory jsou popsané v [deklarace.](declarations-and-definitions-cpp.md) Deklarace může obsahovat více než jeden deklarátor, ale každý deklarátor deklaruje pouze jeden název.  
  
 Následující vzorová deklarace ukazuje, jak kombinace specifikátorů a deklarátorů utváří úplnou deklaraci:  
  
```  
const char *pch, ch;  
```  
  
 V předchozím deklaraci, klíčová slova **const** a `char` tvoří seznam specifikátory. Jsou uvedeny dva deklarátory: `*pch` a `ch`.  Deklarace deklarující několik entit sestává ze specifikátoru typu následovaného čárkou odděleným seznamem deklarátorů ukončeným středníkem.  
  
 **Deklarátory pro jednoduché objekty**  
  
 Deklarátor jednoduchého objektu, například typu int nebo double, je jednoduše jeho název, volitelně se závorkami.  
  
 `int i; // declarator is i`  
  
 `int (i); // declarator is (i)`  
  
 **Deklarátory pro ukazatele, odkazy a pole**  
  
 Operátory ukazatelů vložené před název zajistí, že objekt bude ukazatel nebo reference.   **\***  Operátor deklaruje název jako ukazatel;  **&**  operátor ji deklaruje jako odkaz.  
  
```  
int *i; // declarator is *i  
int **i; // declarator is **i;  
int &i = x; // declaratory is &i  
```  
  
 Připojením klíčového slova `const` nebo `volatile` získá ukazatel tyto speciální vlastnosti.  Použití těchto specifikátorů v deklarátoru (na rozdíl od specifikátoru typu) upravuje vlastnosti ukazatele, nikoli objektu, na který ukazatel ukazuje:  
  
```  
char *const cpc; // const pointer to char   
const char *pcc; // pointer to const char   
const char *const cpcc; // const pointer to const char  
```  
  
 Další informace naleznete v [ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md).  
  
 Ukazatel na člen třídy nebo struktury je deklarován s příslušným zanořeným specifikátorem názvu:  
  
```  
int X::* pIntMember;   
int ::X::* pIntMember; // the initial :: specifies X is in global scope  
char Outer::Inner::* pIntMember; // pointer to char in a nested class  
```  
  
 Závorky uzavírající nepovinný konstantní výraz za názvem přetváří objekt na pole.  Následné závorky deklarují další rozměry pole.  
  
```  
int i[5]; // array with five elements of type int numbered from 0 to 4  
int i[]; // array of unknown size  
char *s[4]; // array of pointers to char  
int i[2][2]; // two dimensional array  
```  
  
 **Deklarátory funkcí**  
  
 Pro deklaraci funkce se používají závorky obsahující seznam argumentů za názvem.  Následující kód deklaruje funkci návratového typu `int` a třemi argumenty typu `int`.  
  
```  
int f(int a, int b, int c);  
```  
  
 Ukazatele a reference na funkce jsou deklarovány přidáním operátoru ukazatele nebo reference před název funkce tak, jak je uvedeno níže.  Obvykle nepovinné závorky jsou vyžadovány pro rozlišení ukazatele na funkci od funkce vracející ukazatel:  
  
```  
int (*pf)(int); // pointer to function returning int  
int *f(int i); // function returning pointer to int  
int (&pf)(int); // reference to function   
```  
  
 Ukazatele na členské funkce jsou odlišeny vnořenými specifikátory názvů:  
  
```  
int (X::* pmf)(); // pointer to member function of X returning int  
int* (X::* pmf)(); // pointer to member function returning pointer to int  
```  
  
 Viz také [ukazatelé na členy](../cpp/pointers-to-members.md).  
  
 **Funkce a objekty ve stejné deklaraci**  
  
 Funkce a objekty lze deklarovat v jedné deklaraci takto:  
  
```  
int i, *j, f(int k);  // int, pointer to int, function returning int  
```  
  
 Syntaxe může být v některých případech matoucí.  Následující deklarace  
  
```  
int* i, f(int k);  // pointer to int, function returning int (not int*)  
```  
  
 může vypadat jako deklarace ukazatele `int` a funkce vracející typ `int*`, ale není tomu tak.  To proto, že operátor * je součástí deklarátoru proměnné `i`, nikoli součástí deklarátoru funkce `f`.  
  
 **Ke zjednodušení syntaxe deklarátoru s – typedef**  
  
 Lepší technikou je však použití direktivy `typedef` nebo kombinace závorek a klíčového slova `typedef`. Vezměte v úvahu deklaraci pole ukazatelů na funkce:  
  
```  
//  Function returning type int that takes one   
//   argument of type char *.  
typedef int (*PIFN)( char * );  
//  Declare an array of 7 pointers to functions   
//   returning int and taking one argument of type   
//   char *.  
PIFN pifnDispatchArray[7];  
```  
  
 Ekvivalentní deklaraci lze napsat bez deklarace `typedef`, je však tak komplikovaná, že riziko chyb převažuje nad všemi výhodami:  
  
```  
int ( *pifnDispatchArray[7] )( char * );  
```  
  
 Další informace o typedef najdete v tématu [aliasy a definice TypeDef](aliases-and-typedefs-cpp.md).  
  
 Ukazatele, reference a pole jednoho základního typu lze v jedné deklaraci kombinovat oddělením čárkami následovně  
  
```  
int a, *b, c[5], **d, &e=a;  
```  
  
 **Složitější syntaxe deklarátoru**  
  
-   Deklarátory ukazatelů, referencí, polí a funkcí lze kombinovat, a určovat tak objekty jako pole ukazatelů na funkce, ukazatele na pole apod.  
  
-   Následující rekurzivní gramatika plně popisuje syntaxi deklarátoru ukazatele.  
  
-   Deklarátor `declarator` je definován jako:  
  
```  
1. identifier   
2. qualified-name   
3. declarator ( argument-list ) [cv-qualfiers] [exception-spec]  
4. declarator [ [ constant-expression ] ]   
  
5. pointer-operatordeclarator   
6. ( declarator )  
```  
  
-   a *ukazatel-– operátor* je jedním z:  
  
```  
  
      * [cv-qualifiers]  
& [cv-qualifiers]  
::nested-name-specifier * [cv-qualfiers]  
```  
  
 Protože může deklarátor obsahovat deklarátory, lze pomocí výše zmíněných pravidel vytvořit složitější odvozené typy jako pole ukazatelů či funkce vracející pole ukazatelů na funkce.  Chcete-li utvořit každý z kroků konstrukce, začněte s identifikátorem představujícím základní datový typ a použijte výše zmíněné pravidlo syntaxe s předchozím výrazem jako deklarátor `declarator`.  Pořadí použití pravidel syntaxe by mělo být opačné oproti způsobu, jak je výraz vyjádřen v angličtině.  Pokud použití *ukazatel-– operátor* syntaxe pravidlo výraz pole nebo funkce závorky lze použít, pokud chcete, aby ukazatel na pole nebo funkce, jako poslední řádek v následující tabulce.  
  
 Následující příklad ukazuje tvorbu „ukazatele na pole 10 ukazatelů na typ int“.  
  
|Slovní vyjádření|Deklarátor|Použité pravidlo syntaxe|  
|-----------------------|----------------|-------------------------|  
||`i`|1|  
|ukazatel(e) na|`*i`|5|  
|pole o 10|`(*i)[10]`|4|  
|ukazatelích na|`*((*i)[10])`|6, a potom 5|  
  
 Při použití většího počtu modifikátorů ukazatelů, referencí, polí nebo funkcí se deklarátory mohou výrazně komplikovat.  Téma [interpretace další složité Deklarátory](../c-language/interpreting-more-complex-declarators.md) popisuje, jak číst složitější syntaxe deklarátoru.  Téma se vztahuje na C a C++, i když v jazyce C++, kdekoli * slouží k označení ukazatel, kvalifikovaný název, jako je například MyClass::\* může použít k určení ukazatel na člena třídy.