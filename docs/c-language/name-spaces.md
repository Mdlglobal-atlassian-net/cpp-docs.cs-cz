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
ms.openlocfilehash: ebf1961d83d14bf95633d4248c2f970c54923274
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325988"
---
# <a name="name-spaces"></a>Obory názvů

Kompilátor vytvoří „obory názvů“ pro rozlišení mezi identifikátory použitými pro různé druhy položek. Názvy v rámci každého oboru názvů musejí být jedinečné, aby nedošlo ke konfliktu, ale stejný název se může objevit ve více než jednom oboru názvů. To znamená, že stejný identifikátor lze použít pro dvě nebo více různých položek za předpokladu, že se položky nacházejí v různých oborech názvů. Kompilátor může rozpoznat odkazy na základě syntaktického kontextu identifikátoru v programu.

> [!NOTE]
> Nezaměňujte omezený pojem jazyka C oboru názvů s funkcí „oboru názvů“ jazyka C++. Zobrazit [obory názvů](../cpp/namespaces-cpp.md) v referenci jazyka C++ pro další informace.

Seznam popisuje obory názvů používané v jazyce C.

Popisky příkazů pojmenované popisků příkazů jsou součástí příkazů. Definice popisků příkazů jsou vždy následovány dvojtečkou, ale nejsou součástí **případ** popisky. Použití popisků příkazů bezprostředně následuje po klíčovém slovu **goto**. Popisky příkazů se nemusejí lišit od jiných názvů nebo od názvů popisků v jiných funkcích.

Značky struktury, sjednocení a výčtu tyto značky jsou součástí struktury, sjednocení a výčtu specifikátory typu a, pokud jsou k dispozici, bezprostředně následují za vyhrazenými slovy **struktura**, **sjednocení**, nebo **výčtu**. Názvy značek musejí být odlišné od všech ostatních značek struktur, výčtu nebo sjednocení se stejnou viditelností.

V oborech názvů přidružených každého typu struktury a sjednocení jsou přidělovány členové struktur nebo sjednocení názvy členů. To znamená, že stejný identifikátor může být názvem součásti v libovolném počtu struktur nebo sjednocení současně. Definice názvů součástí se vždy objevují v rámci typů specifikátorů struktury nebo sjednocení. Použití názvů součásti vždy bezprostředně následuje po operátorů výběru členů (**->** a **.**). Název člena musí být jedinečný v rámci struktury nebo sjednocení, ale nemusí se lišit od jiných názvů v programu, včetně názvů členů různých struktur a sjednocení, případně názvu struktury samotné.

Běžné identifikátory všechny další názvy patří do oboru názvů, který obsahuje proměnné, funkce (včetně formálních parametrů a lokálních proměnných) a konstanty výčtu. Názvy identifikátorů mají vnořenou viditelnost, takže je možné upravit je v rámci bloků.

Názvy typu TypeDef názvy typu Typedef nelze použít jako identifikátory ve stejném oboru.

Protože jsou například značky struktur, členové struktur a názvy proměnných ve třech různých oborech názvů, nedochází ke konfliktu tří různých položek s názvem `student`. Kontext každé položky umožňuje správnou interpretaci pro každý výskyt položky `student` v programu. (Další informace o strukturách naleznete v tématu [deklarace struktur](../c-language/structure-declarations.md).)

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Když `student` se zobrazí po **struktura** – klíčové slovo, ji kompilátor rozpozná jako značku struktury. Když `student` se zobrazí po operátoru výběru členů (**->** nebo **.**), odkazuje název na člena struktury. V jiných kontextech odkazuje položka `student` na proměnnou struktury. Přetížení oboru názvů značek se však nedoporučuje, protože zakrývá význam.

## <a name="see-also"></a>Viz také

[Struktura programu](../c-language/program-structure.md)