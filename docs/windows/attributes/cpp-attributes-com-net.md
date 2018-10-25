---
title: Atributy C++ COM a .NET | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66188f1879c42eaf9429675a2f235130e263211f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072522"
---
# <a name="c-attributes-for-com-and-net"></a>Atributy C++ COM a .NET

Microsoft definuje sadu atributů C++, které zjednodušují programování v modelu COM a rozhraní .NET Framework common language runtime vývoj. Pokud zahrnete atributy ve zdrojových souborech, kompilátor funguje s poskytovatelem knihoven DLL pro vložení kódu nebo změnit kód v souborech generované objektů. Tyto atributy pomáhají při vytváření souborů .idl, rozhraní, knihovny typů a dalších prvků modelu COM. Atributy jsou podporovány v integrovaném vývojovém prostředí (IDE) podle průvodce a v okně Vlastnosti.

Zatímco atributy eliminují některý podrobné psaní kódu, které jsou potřebné pro zápis objektů modelu COM, je nutné na pozadí v [COM Základy](/windows/desktop/com/the-component-object-model) nejlépe jejich použití.

> [!NOTE]
> Pokud chcete pro atributy standard C++, naleznete v tématu [atributy](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Účel atributů

Atributy rozšíření bez narušení classic struktura jazyka C++ v aktuálně možné směry. Atributy umožňují poskytovatelů (samostatné knihovny DLL) rozšíření funkcí jazyka dynamicky. Hlavním cílem atributy je pro zjednodušení vytváření komponent modelu COM, kromě zvýšit úroveň produktivity pro vývojáře komponenty. Atributy lze použít na téměř jakémkoli C++ konstrukce, jako jsou třídy, datové členy nebo členské funkce. Zvýraznění výhody této nové technologie je následující:

- Uvádí známé a jednoduché konvence volání.

- Používá se vložit kód, který na rozdíl od makra, je rozpoznán v ladicím programu.

- Umožňuje snadno odvození ze základních tříd bez nákladných implementace podrobnosti.

- Nahradí velké množství kódu IDL vyžadované komponenty modelu COM s několika stručné atributy.

Například implementovat jednoduché událostní jímka pro obecné třídy ATL, můžete použít [event_receiver](event-receiver.md) atribut pro konkrétní třídu jako `CMyReceiver`. `event_receiver` Atribut je potom kompilovány pomocí kompilátoru jazyka Visual C++, který vloží správný kód do souboru objektu.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Potom můžete nastavit `CMyReceiver` metody `handler1` a `handler2` zpracování událostí (použití vnitřních funkcí [__hook](../../cpp/hook.md)) ze zdroje událostí, které můžete vytvořit pomocí [event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>Základní mechanismy atributů

Existují tři způsoby, jak vložit atributy do projektu. Nejprve můžete je ručně do zdrojového kódu. Za druhé můžete vložit pomocí mřížky vlastností objektu ve vašem projektu. Nakonec můžete vložit pomocí různých průvodců. Další informace o používání **vlastnosti** okno a různých průvodců, najdete v části [vytváření a správa projektů Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md).

Jako dříve, při sestavení projektu, kompilátor analyzuje každý zdrojový soubor jazyka C++, vytváření soubor objektu. Ale když kompilátor narazí atribut, je analyzovat a syntakticky ověřit. Kompilátor poté zavolá dynamicky poskytovatele atributu vložení kódu a provádět další úpravy v době kompilace. Implementace zprostředkovatele se liší v závislosti na typu atributu. Například Atlprov.dll implementují související ATL atributy.

Následující obrázek ukazuje vztah mezi kompilátoru a poskytovatele atributu.

![Atribut komunikace komponent](../media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> Použití atributu nezmění obsah zdrojového souboru. Kód vygenerovaný atributu je viditelné se pouze během relace ladění. Kromě toho pro každý zdrojový soubor v projektu, můžete vygenerovat textový soubor, který zobrazuje výsledky atribut nahrazení. Další informace o tomto postupu najdete v tématu [/Fx (sloučení vloženého kódu)](../../build/reference/fx-merge-injected-code.md) a [ladění vloženého kódu](/visualstudio/debugger/how-to-debug-injected-code).

Jako většina konstruktory jazyka C++ mít atributy sadu vlastností, která definuje jejich správné použití. To se označuje jako kontext atribut a je určena v tabulce atribut kontextu pro každý atribut referenční téma. Například [coclass](coclass.md) atribut lze použít pouze na existující třída nebo struktura, nikoli [cpp_quote –](cpp-quote.md) atribut, který může vložit na libovolné místo v rámci zdrojový soubor jazyka C++.

## <a name="building-an-attributed-program"></a>Sestavení programu s atributy

Poté, co vložíte do zdrojového kódu jazyka Visual C++ atributy, můžete kompilátor Visual C++ k vytvoření souboru typu knihovna a .idl za vás. Následující linkeru možnosti tvorbu souborů .tlb a IDL:

- [/ IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/ IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/ MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/ TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Některé projekty obsahují více souborů .idl nezávislé. Slouží k vytvoření dvou nebo více souborů .tlb a svázat ho Volitelně můžete do bloku prostředků. Tento scénář není aktuálně podporován v jazyce Visual C++.

Kromě toho výstup linkeru jazyka Visual C++ všechny informace o atributu souvisejícím s IDL do jednoho souboru MIDL. Nebude žádný způsob, jak generovat dvě knihovny typů z jednoho projektu.

## <a name="contexts"></a> Kontexty atributů

Atributy C++ lze popsat pomocí čtyři základní pole: cíl se můžou uplatnit na (**platí pro**), pokud jsou opakovatelné nebo ne (**Repeatable**), vyžaduje přítomnost dalších atributů ( **Atributy požadované**) a nekompatibilitu s další atributy (**neplatné atributy**). Tato pole jsou uvedeny v související tabulce v tématu referenční každý atribut. Každá z těchto polí je popsána níže.

### <a name="applies-to"></a>Platí pro

Toto pole popisuje různé prvky jazyka C++, které jsou platné cíle pro zadaného atributu. Například pokud atribut určuje "třída" v **platí pro** pole, to znamená, že atribut lze použít pouze na právní třídu C++. Pokud je atribut použit na členskou funkci třídy, výsledkem bude chyba syntaxe.

Další informace najdete v tématu [atributy podle použití](attributes-by-usage.md).

### <a name="repeatable"></a>Opakovatelné

Toto pole je uvedeno, zda je atribut pro stejný cíl opakovaně použít. Většina atributy nejsou opakovatelné.

### <a name="required-attributes"></a>Vyžadované atributy

Toto pole obsahuje další atributy, které musí být přítomná (který se použije pro stejný cíl) pro zadaný atribut fungovat správně. Je běžné pro atribut, který má obsahovat žádné položky pro toto pole.

### <a name="invalid-attributes"></a>Neplatné atributy

Toto pole obsahuje další atributy, které nejsou kompatibilní se zadaným atributem. Je běžné pro atribut, který má obsahovat žádné položky pro toto pole.

## <a name="in-this-section"></a>V tomto oddílu

[Nejčastější dotazy k programování s atributy](attribute-programming-faq.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Atributy podle použití](attributes-by-usage.md)<br/>
[Abecedně řazená referenční dokumentace k atributům](attributes-alphabetical-reference.md)