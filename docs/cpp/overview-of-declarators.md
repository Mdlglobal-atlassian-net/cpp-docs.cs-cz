---
title: Přehled Deklarátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, about declarators
ms.assetid: 0f2e2312-80bd-4154-8345-718bd9ed2173
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e04b92075e9871ad0cb9e753c472b445b731dbb0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020089"
---
# <a name="overview-of-declarators"></a>Přehled deklarátorů

Deklarátory jsou ty součásti deklarace, které určují názvy objektů a funkcí. Určují také, zda je pojmenovaný objekt objektem, ukazatelem, referencí nebo polem.  Ačkoli deklarátory neurčují základní typ, upravují informace o typu v základním typu a určují tak odvozené typy jako ukazatele, reference a pole.  Deklarátor použitý ve funkci spolupracuje se specifikátorem typu na plném určení návratového typu funkce jako objekt, ukazatel nebo reference. (Specifikátory diskutované v [deklarace a definice](declarations-and-definitions-cpp.md), poskytují informace o vlastnostech, jako je například typ nebo třída úložiště. Modifikátory diskutované v této části a v [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md), upravují deklarátory.) Následující obrázek ukazuje kompletní deklaraci funkce `MyFunction` a označuje komponenty deklarace.

![Modifikátory specifikátorů a deklarátorů](../cpp/media/vc38qy1.gif "vc38QY1") specifikátory, modifikátory a Deklarátory

**Specifické pro Microsoft**

Většinu klíčových slov rozšířených společností Microsoft lze použít jako modifikátory a vytvořit tak odvozené typy. Nejsou to specifikátory ani deklarátory. (Viz [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).)

**Specifické pro END Microsoft**

Deklarátory se vyskytují v syntaxi deklarace za nepovinným seznamem specifikátorů. Těchto specifikátorech pojednává téma [deklarace.](declarations-and-definitions-cpp.md) Deklarace může obsahovat více než jeden deklarátor, ale každý deklarátor deklaruje pouze jeden název.

Následující vzorová deklarace ukazuje, jak kombinace specifikátorů a deklarátorů utváří úplnou deklaraci:

```cpp
const char *pch, ch;
```

V předchozí deklaraci, klíčová slova **const** a **char** tvoří seznam specifikátorů. Jsou uvedeny dva deklarátory: `*pch` a `ch`.  Deklarace deklarující několik entit sestává ze specifikátoru typu následovaného čárkou odděleným seznamem deklarátorů ukončeným středníkem.

**Deklarátory pro jednoduché objekty**

Deklarátor jednoduchého objektu, například typu int nebo double, je jednoduše jeho název, volitelně se závorkami.

`int i; // declarator is i`

`int (i); // declarator is (i)`

**Deklarátory pro ukazatele, reference a pole**

Operátory ukazatelů vložené před název zajistí, že objekt bude ukazatel nebo reference.  <strong>\*</strong> Operátor deklaruje název jako ukazatel; **&** operátor ji deklaruje jako odkaz.

```cpp
int *i; // declarator is *i
int **i; // declarator is **i;
int &i = x; // declaratory is &i
```

Přidávání **const** nebo **volatile** získá ukazatel tyto speciální vlastnosti.  Použití těchto specifikátorů v deklarátoru (na rozdíl od specifikátoru typu) upravuje vlastnosti ukazatele, nikoli objektu, na který ukazatel ukazuje:

```cpp
char *const cpc; // const pointer to char
const char *pcc; // pointer to const char
const char *const cpcc; // const pointer to const char
```

Další informace lze nalézt v [ukazatelé const a volatile](../cpp/const-and-volatile-pointers.md).

Ukazatel na člen třídy nebo struktury je deklarován s příslušným zanořeným specifikátorem názvu:

```cpp
int X::* pIntMember;
int ::X::* pIntMember; // the initial :: specifies X is in global scope
char Outer::Inner::* pIntMember; // pointer to char in a nested class
```

Závorky uzavírající nepovinný konstantní výraz za názvem přetváří objekt na pole.  Následné závorky deklarují další rozměry pole.

```cpp
int i[5]; // array with five elements of type int numbered from 0 to 4
int i[]; // array of unknown size
char *s[4]; // array of pointers to char
int i[2][2]; // two dimensional array
```

**Deklarace pro funkce**

Pro deklaraci funkce se používají závorky obsahující seznam argumentů za názvem.  Následující deklaruje funkci návratového typu **int** a třemi argumenty typu **int**.

```cpp
int f(int a, int b, int c);
```

Ukazatele a reference na funkce jsou deklarovány přidáním operátoru ukazatele nebo reference před název funkce tak, jak je uvedeno níže.  Obvykle nepovinné závorky jsou vyžadovány pro rozlišení ukazatele na funkci od funkce vracející ukazatel:

```cpp
int (*pf)(int); // pointer to function returning int
int *f(int i); // function returning pointer to int
int (&pf)(int); // reference to function
```

Ukazatele na členské funkce jsou odlišeny vnořenými specifikátory názvů:

```cpp
int (X::* pmf)(); // pointer to member function of X returning int
int* (X::* pmf)(); // pointer to member function returning pointer to int
```

Viz také [ukazatelů na členy](../cpp/pointers-to-members.md).

**Funkce a objekty v jedné deklaraci**

Funkce a objekty lze deklarovat v jedné deklaraci takto:

```cpp
int i, *j, f(int k);  // int, pointer to int, function returning int
```

Syntaxe může být v některých případech matoucí.  Následující deklarace

```cpp
int* i, f(int k);  // pointer to int, function returning int (not int*)
```

může vypadat jako deklarace **int** ukazatele a funkci vracející `int*`, ale není to.  Důvodem je, \* je součástí deklarátoru `i`, nikoli součástí deklarátoru `f`.

**Zjednodušení syntaxe deklarátoru pomocí direktivy typedef**

Lepší technikou je však použití **typedef** nebo kombinace závorek a **typedef** – klíčové slovo. Vezměte v úvahu deklaraci pole ukazatelů na funkce:

```cpp
//  Function returning type int that takes one
//   argument of type char *.
typedef int (*PIFN)( char * );
//  Declare an array of 7 pointers to functions
//   returning int and taking one argument of type
//   char *.
PIFN pifnDispatchArray[7];
```

Ekvivalentní deklaraci lze napsat bez **typedef** deklaraci, ale je to složité, riziko chyb převažuje veškeré výhody:

```cpp
int ( *pifnDispatchArray[7] )( char * );
```

Další informace o typedef naleznete v tématu [aliasy a definice TypeDef](aliases-and-typedefs-cpp.md).

Ukazatele, reference a pole jednoho základního typu lze v jedné deklaraci kombinovat oddělením čárkami následovně

```cpp
int a, *b, c[5], **d, &e=a;
```

**Složitější syntaxe deklarátoru**

- Deklarátory ukazatelů, referencí, polí a funkcí lze kombinovat, a určovat tak objekty jako pole ukazatelů na funkce, ukazatele na pole apod.

- Následující rekurzivní gramatika plně popisuje syntaxi deklarátoru ukazatele.

- Deklarátor `declarator` je definován jako:

  - identifikátor 
  - kvalifikovaný název 
  - deklarátor (seznam argumentů) [qualfiers cv] [výjimka – specifikace]
  - deklarátor [[konstantního výrazu.]]
  - deklarátoru ukazatele-– operátor 
  - (deklarátor)

- a *operátoru ukazatele* patří:

  - \* [kvalifikátory cv]
  - & [kvalifikátory cv]:: vnořené specifikátorem názvu \* [kvalifikátory cv]

Protože může deklarátor obsahovat deklarátory, lze pomocí výše zmíněných pravidel vytvořit složitější odvozené typy jako pole ukazatelů či funkce vracející pole ukazatelů na funkce.  Chcete-li utvořit každý z kroků konstrukce, začněte s identifikátorem představujícím základní datový typ a použijte výše zmíněné pravidlo syntaxe s předchozím výrazem jako deklarátor `declarator`.  Pořadí použití pravidel syntaxe by mělo být opačné oproti způsobu, jak je výraz vyjádřen v angličtině.  Pokud použití *operátoru ukazatele* pravidlo syntaxe na výraz pole nebo funkce použít závorky, pokud má ukazatel na pole nebo funkce, jako poslední řádek v tabulce níže.

Následující příklad ukazuje tvorbu „ukazatele na pole 10 ukazatelů na typ int“.

|Slovní vyjádření|Deklarátor|Použité pravidlo syntaxe|
|-----------------------|----------------|-------------------------|
||`i`|1|
|ukazatel(e) na|`*i`|5|
|pole o 10|`(*i)[10]`|4|
|ukazatelích na|`*((*i)[10])`|6, a potom 5|

Při použití většího počtu modifikátorů ukazatelů, referencí, polí nebo funkcí se deklarátory mohou výrazně komplikovat.  Téma [interpretace složitějších Deklarátorů](../c-language/interpreting-more-complex-declarators.md) popisuje, jak číst složitější syntaxi deklarátorů.  Téma se vztahuje na C a C++, ačkoli v jazyce C++, kdekoli \* se používá k označení ukazatel, úplný název, například MyClass::\* slouží k určení ukazatele na člen třídy.