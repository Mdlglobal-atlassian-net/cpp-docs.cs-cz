---
title: Prototypy funkcí
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: 2c75db3e1550927af57054a2cc1561d9df1567a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233125"
---
# <a name="function-prototypes"></a>Prototypy funkcí

Deklarace funkce předchází definici funkce a určuje název, návratový typ, třída úložiště a další atributy funkce. Jako prototyp potřeba deklaraci funkce také vytvořit typy a identifikátory pro argumenty funkce.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *sekvence atributů*<sub>optimalizované</sub> *init-declarator-list*<sub>optimalizované</sub> **;**

/\* *sekvence atributů*<sub>optimalizované</sub> je specifické pro Microsoft \*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=** *inicializátor*

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*přímé declarator*: /\* deklarátorem funkce \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**   / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

Prototyp má stejný formulář jako definice funkce, s tím rozdílem, že je ukončeno prvkem středníkem hned za pravou závorku a proto nemá žádný text. V obou případech musíte návratový typ souhlasit s návratovým typem zadaným v definici funkce.

Prototypy funkcí mají důležité následovně:

- Navázání návratový typ funkce, které vrací typy jiné než **int**. I když funkce, které vracejí **int** hodnoty nevyžadují prototypů, se doporučuje prototypů.

- Bez dokončení prototypů jsou provedeny standardní převody, ale je proveden žádný pokus o zkontrolujte typ a počet argumentů počtem parametrů.

- Prototypy slouží k inicializaci ukazatele na funkce, než tyto funkce jsou definovány.

- Seznam parametrů slouží ke kontrole souvztažnost argumentů ve volání funkce s parametry v definici funkce.

Převedený typ každý parametr určuje výklad argumenty volání funkce umístí v zásobníku. Neshoda typů mezi argumentu a parametru může způsobit argumenty v zásobníku do dojít k nesprávné interpretaci. Například v počítači se 16 bitů, pokud ukazatel 16 bitů je předán jako argument, potom deklarovat jako **dlouhé** parametr, jako jsou interpretovány prvních 32 bitů v zásobníku **dlouhé** parametr. Tato chyba vytvoří problémy nejen s **dlouhé** parametr, ale s parametry, které na něho. Můžete zjistit chyby tohoto druhu deklarace prototypů úplné funkce pro všechny funkce.

Prototyp vytváří atributy funkce tak, aby volání funkce, které předcházet jeho definice (nebo v jiných zdrojových souborech dojde k) můžete zkontrolovat typ argumentu a návratový typ neshody. Pokud zadáte například **statické** specifikátor třídy úložiště v prototypu, musíte zadat také **statické** třídu úložiště v definici funkce.

Dokončení deklarací parametrů (`int a`) lze kombinovat s abstraktní deklarátory (`int`) ve stejné deklaraci. Například následující deklaraci je možné:

```C
int add( int a, int );
```

Prototyp může obsahovat typ i identifikátor pro každý výraz, který je předán jako argument. Tyto identifikátory však mít rozsah pouze do konce deklarace. Prototyp můžete také sledovat, skutečnost, že je počet argumentů proměnné nebo předány žádné argumenty. Bez seznamu nemusí být odhalena neshody, proto kompilátor nemůže generovat diagnostické zprávy, které se jich týkají. Zobrazit [argumenty](../c-language/arguments.md) Další informace o kontrolu typu.

Rozsah prototypu v kompilátor Microsoft C je vyhovující standardu ANSI nyní při kompilaci s **/Za** – možnost kompilátoru. To znamená, že pokud deklarujete **struktura** nebo **sjednocení** značky v prototypu, značky se zadá v daném oboru, spíše než v globálním oboru. Například při kompilaci s **/Za** ANSI dodržování předpisů, můžete nikdy volat tuto funkci bez chyba neshody typu:

```C
void func1( struct S * );
```

Chcete-li váš kód, definice nebo deklarace **struktura** nebo **sjednocení** v globálním oboru před prototyp funkce:

```C
struct S;
void func1( struct S * );
```

V části **/Ze**, značky se stále zadá v globálním oboru.

## <a name="see-also"></a>Viz také:

[Funkce](../c-language/functions-c.md)
