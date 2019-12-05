---
title: Používání příkazů dllimport a dllexport ve třídách jazyka C++
ms.date: 11/04/2016
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
ms.openlocfilehash: b42ba7c1a88a4de28eb3385bbf6cad068abf1944
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857226"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Používání příkazů dllimport a dllexport ve třídách jazyka C++

**Specifické pro společnost Microsoft**

Můžete deklarovat C++ třídy s atributem **dllimport** nebo **dllexport** . Tyto formy vyjadřuje, že je celá třída importovaná nebo exportovaná. Třídy exportované tímto způsobem se nazývají exportovatelné třídy.

Následující příklad definuje exportovatelnou třídu. Všechny členské funkce a statická data jsou exportovány:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Všimněte si, že explicitní použití atributů **dllimport** a **dllexport** u členů exportovatelných tříd je zakázáno.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Třídy dllexport

Pokud deklarujete třídu **dllexport**, jsou exportovány všechny členské funkce a statické datové členy. Musíte zadat definice všech těchto členů ve stejném programu. Jinak dojde k chybě propojovacího programu. Jedinou výjimkou z tohoto pravidla platí pro čistě virtuální funkce, pro které nemusíte poskytnout explicitní definice. Protože však destruktor abstraktní třídy je vždy volán destruktorem základní třídy, čistě virtuální destruktory musí vždy poskytnout definici. Všimněte si, že tato pravidla jsou stejné pro neexportovatelné třídy.

Pokud exportujete data typu nebo funkce třídy, které vracejí třídy, je nutné exportovat třídy.

##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>Třídy dllimport

Pokud deklarujete třídu **dllimport**, jsou importovány všechny členské funkce a statické datové členy. Na rozdíl od chování **dllimport** a **dllexport** u netříděných typů nemohou statické datové členy určovat definici ve stejném programu, ve kterém je definována třída **dllimport** .

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Dědičnost a exportovatelné třídy

Všechny základní třídy exportovatelné třídy musí být exportovatelné. V opačném případě bude vyvoláno upozornění kompilátoru. Kromě toho musí být možné exportovat také všechny dostupné členy, kteří jsou zároveň třídami. Toto pravidlo povoluje, aby třída **dllexport** dědila z třídy **dllimport** a třídu **dllimport** , která dědí z třídy **dllexport** (i když se druhá nedoporučuje). Je pravidlem, že vše, co je přístupné pro klienta knihovny DLL (podle pravidel přístupu jazyka C++), by mělo být součástí rozhraní, které lze exportovat. Jedná se o privátní členy dat zmiňované ve vložených funkcích.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Import/export selektivních členů

Vzhledem k tomu, že členské funkce a statická data ve třídě mají implicitně vnější propojení, můžete je deklarovat pomocí atributu **dllimport** nebo **dllexport** , pokud není exportována celá třída. Pokud je celá třída importovaná nebo exportovaná, je zakázaná explicitní deklarace členských funkcí a dat jako **dllimport** nebo **dllexport** . Pokud deklarujete statického datového členu v rámci definice třídy jako **dllexport**, musí se definice nacházet někde v rámci stejného programu (stejně jako u vnějšího propojení netřídy).

Podobně můžete deklarovat členské funkce pomocí atributů **dllimport** nebo **dllexport** . V takovém případě je nutné zadat definici **dllexport** někam do stejného programu.

Je vhodné si uvědomit několik důležitých bodů týkajících se importu a exportu selektivních členů:

- Import a export výběrových členů je nejvhodnější pro poskytování verze exportované třídy rozhraní, která je více omezující, tedy taková, pro kterou můžete navrhnout knihovnu DLL, která omezí viditelnost veřejných a soukromých funkcí, které by jazyk jinak neomezil. Je také vhodný pro optimalizaci exportovatelného rozhraní: pokud víte, že klient podle definice nelze získat přístup k některým osobním datům, není nutné exportovat celé třídy.

- Při exportu jedné virtuální funkce ve třídě můžete exportovat všechny nebo poskytnout alespoň verze, které může klient použít přímo.

- Pokud máte třídu, ve které používáte selektivní členské import/export s virtuálními funkcemi, funkce musí být v rozhraní exportovatelné nebo definované jako inline (viditelné pro klienta).

- Pokud definujete člena jako **dllexport** , ale nezahrnete ho do definice třídy, je vygenerována chyba kompilátoru. Musíte definovat člena v záhlaví třídy.

- I když je povolena definice členů třídy jako **dllimport** nebo **dllexport** , nelze přepsat rozhraní zadané v definici třídy.

- Definujete-li členskou funkci na jiném místě než tělo definice třídy, ve které jste ji deklarovali, je vygenerováno upozornění, pokud je funkce definována jako **dllexport** nebo **dllimport** (Pokud se tato definice liší od, která je zadána v deklaraci třídy).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[dllexport, dllimport](../cpp/dllexport-dllimport.md)