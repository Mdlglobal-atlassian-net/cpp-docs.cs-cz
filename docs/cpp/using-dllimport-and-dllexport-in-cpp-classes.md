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
ms.openlocfilehash: 7d67660fa3b5d57c56d02d5526f0a9ea294a8eef
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187827"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Používání příkazů dllimport a dllexport ve třídách jazyka C++

**Specifické pro společnost Microsoft**

Můžete deklarovat C++ třídy s atributem **dllimport** nebo **dllexport** . Tyto formuláře naznačují, že je celá třída importovaná nebo exportovaná. Třídy exportované tímto způsobem se nazývají exportovatelné třídy.

Následující příklad definuje exportovatelné třídy. Exportují se všechny jeho členské funkce a statická data:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Všimněte si, že explicitní použití atributů **dllimport** a **dllexport** u členů exportovatelných tříd je zakázáno.

##  <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Třídy dllexport

Pokud deklarujete třídu **dllexport**, jsou exportovány všechny členské funkce a statické datové členy. Je nutné poskytnout definice všech takových členů ve stejném programu. V opačném případě je vygenerována chyba linkeru. Jedinou výjimkou z tohoto pravidla se vztahuje na čistě virtuální funkce, pro které nemusíte zadávat explicitní definice. Vzhledem k tomu, že destruktor abstraktní třídy je vždy volán destruktorem pro základní třídu, čistě virtuální destruktory musí vždy poskytnout definici. Všimněte si, že tato pravidla jsou stejná pro neexportované třídy.

Pokud exportujete data typu třídy nebo funkce vracející třídy, nezapomeňte exportovat třídu.

##  <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>Třídy dllimport

Pokud deklarujete třídu **dllimport**, jsou importovány všechny členské funkce a statické datové členy. Na rozdíl od chování **dllimport** a **dllexport** u netříděných typů nemohou statické datové členy určovat definici ve stejném programu, ve kterém je definována třída **dllimport** .

##  <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Dědičnost a exportovatelné třídy

Všechny základní třídy exportovatelné třídy musí být exportovatelné. V takovém případě se vygeneruje upozornění kompilátoru. Kromě toho musí být exportovatelné všechny přístupné členy, které jsou také třídy. Toto pravidlo povoluje, aby třída **dllexport** dědila z třídy **dllimport** a třídu **dllimport** , která dědí z třídy **dllexport** (i když se druhá nedoporučuje). Jako pravidlo, vše, co je přístupné pro klienta knihovny DLL (podle pravidel C++ přístupu), by mělo být součástí exportovatelné rozhraní. To zahrnuje soukromé datové členy, na které se odkazuje ve vložených funkcích.

##  <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Import/export selektivních členů

Vzhledem k tomu, že členské funkce a statická data ve třídě mají implicitně vnější propojení, můžete je deklarovat pomocí atributu **dllimport** nebo **dllexport** , pokud není exportována celá třída. Pokud je celá třída importovaná nebo exportovaná, je zakázaná explicitní deklarace členských funkcí a dat jako **dllimport** nebo **dllexport** . Pokud deklarujete statického datového členu v rámci definice třídy jako **dllexport**, musí se definice nacházet někde v rámci stejného programu (stejně jako u vnějšího propojení netřídy).

Podobně můžete deklarovat členské funkce pomocí atributů **dllimport** nebo **dllexport** . V takovém případě je nutné zadat definici **dllexport** někam do stejného programu.

Je vhodné si uvědomit několik důležitých bodů týkajících se importu a exportu z selektivního člena:

- Import/export selektivního člena se nejlépe používá pro poskytnutí verze exportovaného rozhraní třídy, které je více omezující. To znamená, že jeden, pro který můžete navrhnout knihovnu DLL, která zveřejňuje méně veřejných a privátních funkcí, než by jinak povolovala. Je také užitečné pro optimalizaci rozhraní, které lze exportovat: Pokud víte, že klient, podle definice, nemá přístup k některým soukromým datům, není nutné exportovat celou třídu.

- Pokud exportujete jednu virtuální funkci ve třídě, je nutné exportovat všechny z nich nebo alespoň poskytnout verze, které může klient použít přímo.

- Máte-li třídu, ve které používáte selektivní člen import/export s virtuálními funkcemi, funkce musí být v rozhraní, které lze exportovat nebo které je definováno jako vložené (viditelné pro klienta).

- Pokud definujete člena jako **dllexport** , ale nezahrnete ho do definice třídy, je vygenerována chyba kompilátoru. Je nutné definovat člena v hlavičce třídy.

- I když je povolena definice členů třídy jako **dllimport** nebo **dllexport** , nelze přepsat rozhraní zadané v definici třídy.

- Definujete-li členskou funkci na jiném místě než tělo definice třídy, ve které jste ji deklarovali, je vygenerováno upozornění, pokud je funkce definována jako **dllexport** nebo **dllimport** (Pokud se tato definice liší od, která je zadána v deklaraci třídy).

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
