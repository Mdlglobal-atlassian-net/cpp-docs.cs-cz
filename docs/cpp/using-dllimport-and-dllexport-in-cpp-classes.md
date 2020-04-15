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
ms.openlocfilehash: c0a2c96a37f58c956976980beafd5ecbed4d1318
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365122"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Používání příkazů dllimport a dllexport ve třídách jazyka C++

**Specifické pro Microsoft**

Můžete deklarovat třídy Jazyka C++ s atributem **dllimport** nebo **dllexport.** Tyto formuláře znamenají, že celá třída je importována nebo exportována. Třídy exportované tímto způsobem se nazývají exportovatelné třídy.

Následující příklad definuje exportovatelnou třídu. Exportují se všechny členské funkce a statická data:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Všimněte si, že explicitní použití **dllimport** a **dllexport** atributy na členy exportovatelné třídy je zakázáno.

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>třídy dllexportu

Když deklarujete **dllexport**třídy , exportují se všechny její členské funkce a statické datové členy. Je nutné zadat definice všech těchto členů ve stejném programu. V opačném případě je generována chyba propojovacího propojení. Jedinou výjimkou z tohoto pravidla platí pro čisté virtuální funkce, pro které není nutné zadat explicitní definice. Protože však destruktor pro abstraktní třídu je vždy volán destruktorem pro základní třídu, musí vždy poskytovat definici čisté virtuální destruktory. Všimněte si, že tato pravidla jsou stejné pro neexportovatelné třídy.

Pokud exportujete data typu třídy nebo funkcí, které vracejí třídy, nezapomeňte exportovat třídu.

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>třídy dllimport

Když deklarujete **dllimport**třídy , importují se všechny její členské funkce a statické datové členy. Na rozdíl od chování **dllimport** a **dllexport** u typů netříd, statické datové členy nelze zadat definici ve stejném programu, ve kterém je definována třída **dllimport.**

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Třídy dědičnosti a exportu

Všechny základní třídy exportovatelné třídy musí být exportovatelné. Pokud tomu tak není, je generováno upozornění kompilátoru. Kromě toho musí být všechny přístupné členy, které jsou také třídy musí být exportovatelné. Toto pravidlo umožňuje **dllexport** třídy dědit z **dllimport** třídy a **dllimport** třídy dědit z **dllexport** třídy (i když se nedoporučuje). Je pravidlem, že vše, co je přístupné klientovi knihovny DLL (podle pravidel přístupu jazyka C++) by mělo být součástí exportovatelného rozhraní. To zahrnuje soukromé datové členy odkazované v vslaných funkcích.

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektivní import/export členů

Vzhledem k tomu, že členské funkce a statická data v rámci třídy mají implicitně externí propojení, můžete je deklarovat s atributem **dllimport** nebo **dllexport,** pokud není exportována celá třída. Pokud je importována nebo exportována celá třída, je zakázáno explicitní prohlášení členských funkcí a dat jako **dllimport** nebo **dllexport.** Pokud deklarujete statický datový člen v rámci definice třídy jako **dllexport**, musí se definice vyskytovat někde ve stejném programu (jako u externího propojení mimo třídu).

Podobně můžete deklarovat členské funkce s atributy **dllimport** nebo **dllexport.** V takovém případě je nutné zadat definici **dllexport** někde ve stejném programu.

Stojí za to poznamenat několik důležitých bodů týkajících se selektivního dovozu a vývozu členů:

- Selektivní import/export členů se nejlépe používá k poskytnutí verze exportovaného rozhraní třídy, která je více omezující; to znamená, že jeden, pro který můžete navrhnout DLL, která zveřejňuje méně veřejných a soukromých funkcí, než by jinak jazyk povolit. Je také užitečné pro jemné doladění exportovatelné rozhraní: pokud víte, že klient, podle definice, není schopen získat přístup k některým soukromým datům, není nutné exportovat celou třídu.

- Pokud exportujete jednu virtuální funkci ve třídě, musíte exportovat všechny nebo alespoň poskytnout verze, které může klient přímo používat.

- Pokud máte třídu, ve které používáte selektivní členské import/export s virtuálními funkcemi, funkce musí být v exportovatelné rozhraní nebo definované vřádku (viditelné pro klienta).

- Pokud definujete člen jako **dllexport,** ale nezahrnete jej do definice třídy, je generována chyba kompilátoru. Je nutné definovat člena v záhlaví třídy.

- Přestože je povolena definice členů třídy jako **dllimport** nebo **dllexport,** nelze přepsat rozhraní zadané v definici třídy.

- Pokud definujete členskou funkci na jiném místě než v těle definice třídy, ve kterém jste ji deklarovali, je generováno upozornění, pokud je funkce definována jako **dllexport** nebo **dllimport** (pokud se tato definice liší od definice uvedené v deklaraci třídy).

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
