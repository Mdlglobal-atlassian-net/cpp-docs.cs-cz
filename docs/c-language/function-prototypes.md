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
ms.openlocfilehash: 9c42ce5b23e6f755dafd57bdb5a5f79cf1adb4ec
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857083"
---
# <a name="function-prototypes"></a>Prototypy funkcí

Deklarace funkce předchází definici funkce a určuje název, návratový typ, třídu úložiště a další atributy funkce. Aby byl prototyp, deklarace funkce musí také vytvořit typy a identifikátory pro argumenty funkce.

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – atribut specifikátors* *-SEQ*<sub>opt</sub> *init-deklarátor-list*<sub>opt</sub> **;**

/\**atribut-seq*<sub>opt</sub> je specifický pro společnost Microsoft\*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*init-deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor-list*  **,**  *init-deklarátor*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicializátor* deklarátor

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*Direct-deklarátor*:/\* A – funkce deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(***parametr-Type-list***)**   / \* – nový styl deklarátor      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor***(opt***-list*<sub>opt</sub> **)**  / \* zastaralý styl deklarátor    \*/

Prototyp má stejný tvar jako definice funkce, s tím rozdílem, že je ukončen středníkem hned za pravou závorku a proto nemá žádné tělo. V obou případech musí návratový typ souhlasit s návratovým typem zadaným v definici funkce.

Prototypy funkcí mají následující důležité použití:

- Navážou návratový typ pro funkce, které vracejí jiné typy než **int**. I když funkce, které vracejí hodnoty typu **int** , nevyžadují prototypy, jsou doporučeny prototypy.

- Bez kompletních prototypů jsou provedeny standardní převody, ale není proveden žádný pokus o kontrolu typu nebo počtu argumentů s počtem parametrů.

- Prototypy se používají k inicializaci ukazatelů na funkce před definováním těchto funkcí.

- Seznam parametrů se používá ke kontrole korespondence argumentů ve volání funkce s parametry v definici funkce.

Převedený typ každého parametru určuje interpretaci argumentů, které volání funkce umístí do zásobníku. Neshoda typů mezi argumentem a parametrem může způsobit, že argumenty v zásobníku budou špatně interpretovány. Například v 16bitovém počítači, pokud je 16bitový ukazatel předán jako argument a následně deklarován jako **dlouhý** parametr, prvních 32 bitů v zásobníku je interpretováno jako **dlouhý** parametr. Tato chyba vytvoří pouze problémy s parametrem **Long** , ale s parametry, které následují. Chyby tohoto typu můžete zjistit deklarováním kompletních prototypů funkcí pro všechny funkce.

Prototyp vytvoří atributy funkce tak, aby volání funkce, která předchází příslušné definici (nebo k ní dochází v jiných zdrojových souborech), mohla být kontrolována pro neshody typu argumentů a návratového typu. Například pokud v prototypu zadáte specifikátor třídy úložiště **static** , je nutné v definici funkce také zadat třídu **statického** úložiště.

Kompletní deklarace parametrů (`int a`) lze kombinovat s abstraktním deklarátory (`int`) ve stejné deklaraci. Například následující deklarace je platná:

```C
int add( int a, int );
```

Prototyp může zahrnovat jak typ, tak identifikátor pro, každý výraz, který je předán jako argument. Nicméně takové identifikátory mají rozsah pouze do konce deklarace. Prototyp může také odrážet skutečnost, že počet argumentů je proměnná nebo že nejsou předány žádné argumenty. Bez takového seznamu nelze zobrazit neshody, takže kompilátor nemůže generovat diagnostické zprávy týkající se těchto seznamů. Další informace o kontrole typů naleznete v tématu [argumenty](../c-language/arguments.md) .

Obor prototypu v kompilátoru jazyka Microsoft C je nyní kompatibilní se standardem ANSI při kompilaci s možností kompilátoru **/za** . To znamená, že pokud deklarujete značku **struktury** nebo **sjednocení** v rámci prototypu, je značka zadána v tomto oboru, nikoli v globálním rozsahu. Například při kompilování s **/za** pro kompatibilitu se standardem ANSI nemůžete tuto funkci nikdy volat bez toho, aby došlo k chybě neshody typů:

```C
void func1( struct S * );
```

Chcete-li opravit kód, definujte nebo deklarujte **strukturu** nebo **sjednocení** v globálním oboru před prototypem funkce:

```C
struct S;
void func1( struct S * );
```

V části **/ze**je značka stále zadána v globálním rozsahu.

## <a name="see-also"></a>Viz také

[Functions](../c-language/functions-c.md)
