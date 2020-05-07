---
title: Obory názvů
ms.date: 11/04/2016
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
ms.openlocfilehash: 76ad9b797a4f192e8f22f8c040f5a308371a461b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325764"
---
# <a name="name-spaces"></a>Obory názvů

Kompilátor vytvoří „obory názvů“ pro rozlišení mezi identifikátory použitými pro různé druhy položek. Názvy v rámci každého oboru názvů musejí být jedinečné, aby nedošlo ke konfliktu, ale stejný název se může objevit ve více než jednom oboru názvů. To znamená, že stejný identifikátor lze použít pro dvě nebo více různých položek za předpokladu, že se položky nacházejí v různých oborech názvů. Kompilátor může rozpoznat odkazy na základě syntaktického kontextu identifikátoru v programu.

> [!NOTE]
> Nezaměňujte omezený pojem jazyka C oboru názvů s funkcí „oboru názvů“ jazyka C++. Další informace najdete v tématu [obory názvů](../cpp/namespaces-cpp.md) v referenční příručce jazyka C++.

Seznam popisuje obory názvů používané v jazyce C.

Popisky příkazů pojmenované příkazy jsou součástí příkazů. Definice popisků příkazů jsou vždycky následovány dvojtečkou, ale nejsou součástí popisků **case** . Použití popisků příkazů vždy následuje po klíčovém slovu **goto**. Popisky příkazů se nemusejí lišit od jiných názvů nebo od názvů popisků v jiných funkcích.

Značky struktury, sjednocení a výčtu: tyto značky jsou součástí specifikátoru typu struktury, sjednocení a výčtu, a pokud jsou k dispozici, vždy bezprostředně postupujte podle **struktury**vyhrazených slov, **sjednocení**nebo **výčtu**. Názvy značek musejí být odlišné od všech ostatních značek struktur, výčtu nebo sjednocení se stejnou viditelností.

Členy struktur nebo názvů členů sjednocení jsou přidělovány v názvových prostorech přidružených k jednotlivým typům struktury a sjednocení. To znamená, že stejný identifikátor může být názvem součásti v libovolném počtu struktur nebo sjednocení současně. Definice názvů součástí se vždy objevují v rámci typů specifikátorů struktury nebo sjednocení. Použití názvů komponent vždy následuje po operátorech výběru členů (**->** a **.**). Název člena musí být jedinečný v rámci struktury nebo sjednocení, ale nemusí se lišit od jiných názvů v programu, včetně názvů členů různých struktur a sjednocení, případně názvu struktury samotné.

Běžné identifikátory všechny ostatní názvy spadají do oboru názvů, který obsahuje proměnné, funkce (včetně formálních parametrů a místních proměnných) a konstanty výčtu. Názvy identifikátorů mají vnořenou viditelnost, takže je možné upravit je v rámci bloků.

Definice typedef názvy typedef nelze použít jako identifikátory ve stejném oboru.

Protože jsou například značky struktur, členové struktur a názvy proměnných ve třech různých oborech názvů, nedochází ke konfliktu tří různých položek s názvem `student`. Kontext každé položky umožňuje správnou interpretaci pro každý výskyt položky `student` v programu. (Informace o strukturách naleznete v tématu [deklarace struktury](../c-language/structure-declarations.md).)

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Když `student` se zobrazí po klíčovém slově **struct** , kompilátor ho rozpoznává jako značku struktury. Když `student` se zobrazí po operátoru výběru členů (**->** nebo **.**), název odkazuje na člen struktury. V jiných kontextech odkazuje položka `student` na proměnnou struktury. Přetížení oboru názvů značek se však nedoporučuje, protože zakrývá význam.

## <a name="see-also"></a>Viz také

[Struktura programu](../c-language/program-structure.md)
