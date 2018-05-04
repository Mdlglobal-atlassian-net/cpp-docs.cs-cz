---
title: Název prostory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b0fe8a097da3de67d149665928524395988c730
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="name-spaces"></a>Obory názvů
Kompilátor vytvoří „obory názvů“ pro rozlišení mezi identifikátory použitými pro různé druhy položek. Názvy v rámci každého oboru názvů musejí být jedinečné, aby nedošlo ke konfliktu, ale stejný název se může objevit ve více než jednom oboru názvů. To znamená, že stejný identifikátor lze použít pro dvě nebo více různých položek za předpokladu, že se položky nacházejí v různých oborech názvů. Kompilátor může rozpoznat odkazy na základě syntaktického kontextu identifikátoru v programu.  
  
> [!NOTE]
>  Nezaměňujte omezený pojem jazyka C oboru názvů s funkcí „oboru názvů“ jazyka C++. V tématu [obory názvů](../cpp/namespaces-cpp.md) v C *++ referenční informace k jazyku* Další informace.  
  
 Seznam popisuje obory názvů používané v jazyce C.  
  
 Popisky příkazů  
 Popisky příkazů obsahující název jsou součástí příkazů. Definice příkaz popisky jsou vždy následovaný dvojtečkou ale nejsou součástí jsou **případ** popisky. Použití popisků příkazů bezprostředně následuje po klíčovém slovu `goto`. Popisky příkazů se nemusejí lišit od jiných názvů nebo od názvů popisků v jiných funkcích.  
  
 Značky struktury, sjednocení a výčtu  
 Tyto značky jsou součástí struktury, sjednocení a výčet specifikátory typu a pokud je k dispozici, vždy okamžitě postupujte podle vyhrazená slova `struct`, **sjednocení**, nebo `enum`. Názvy značek musejí být odlišné od všech ostatních značek struktur, výčtu nebo sjednocení se stejnou viditelností.  
  
 Členové struktur nebo sjednocení  
 V oborech názvů přidružených ke každému typu struktury a sjednocení jsou přidělovány názvy členů. To znamená, že stejný identifikátor může být názvem součásti v libovolném počtu struktur nebo sjednocení současně. Definice názvů součástí se vždy objevují v rámci typů specifikátorů struktury nebo sjednocení. Používá vždy názvům součástí bezprostředně následující operátory výběru členů (**->** a **.**). Název člena musí být jedinečný v rámci struktury nebo sjednocení, ale nemusí se lišit od jiných názvů v programu, včetně názvů členů různých struktur a sjednocení, případně názvu struktury samotné.  
  
 Běžné identifikátory  
 Všechny další názvy patří do oboru názvů, který obsahuje proměnné, funkce (včetně formálních parametrů a lokálních proměnných) a konstanty výčtů. Názvy identifikátorů mají vnořenou viditelnost, takže je možné upravit je v rámci bloků.  
  
 Názvy typu Typedef  
 Názvy typu Typedef nelze ve stejném oboru použít jako identifikátory.  
  
 Protože jsou například značky struktur, členové struktur a názvy proměnných ve třech různých oborech názvů, nedochází ke konfliktu tří různých položek s názvem `student`. Kontext každé položky umožňuje správnou interpretaci pro každý výskyt položky `student` v programu. (Informace o struktury najdete v tématu [deklarace struktury](../c-language/structure-declarations.md).)  
  
```  
struct student {  
   char student[20];  
   int class;  
   int id;  
   } student;  
```  
  
 V případě zobrazení položky `student` za klíčovým slovem `struct` ji kompilátor rozpozná jako značku struktury. Když `student` se zobrazí po výběru členů operátoru (**->** nebo **.**), název odkazuje na člena struktura. V jiných kontextech odkazuje položka `student` na proměnnou struktury. Přetížení oboru názvů značek se však nedoporučuje, protože zakrývá význam.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu](../c-language/program-structure.md)