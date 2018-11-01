---
title: Omezení názvu symbolu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.restrictions.name
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
ms.openlocfilehash: 7b6d8804dc7f3c9768dc9e86fde0e708f67c43fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624851"
---
# <a name="symbol-name-restrictions"></a>Omezení názvu symbolu

Omezení pro názvy symbolů jsou následující:

- Všechny [symboly](../windows/symbols-resource-identifiers.md) musí být jedinečné v rámci oboru aplikace. To zabraňuje konfliktní definice symbolu v souborech hlaviček.

- Platné znaky pro název symbolu zahrnout, A-Z, a – z, 0-9 a podtržítka (_).

- Názvy symbolů nemůže začínat číslem a jsou omezené na 247 znaků.

- Názvy symbolů nesmí obsahovat mezery.

- Názvy symbolů nejsou velká a malá písmena, ale je zachováno případ prvním definice symbolu. Hlavičkový soubor, který definuje symboly umožňuje kompilátoru/editor prostředků a programech C++ odkazovat prostředky definované v souboru prostředků. Pro dva názvy symbolů, která se liší pouze v případě, program jazyka C++ se zobrazí dva samostatné symboly, zatímco kompilátor/editor prostředků se zobrazí oba názvy jako odkazující na jeden jeden symbol.

   > [!NOTE]
   > Pokud není podle schématu název standardní symbol (ID*_[keyword]) uvedených níže, a být stejná jako klíčové slovo ví, kompilátor prostředků skriptu, došlo k pokusu o vytvoření souboru skriptu prostředků bude výsledkem chyba zdánlivě náhodný název symbolu se stane s generace, které je obtížné diagnostikovat. Chcete-li tomu zabránit, dodržovat standardní schéma pojmenování.

Názvy symbolů mají popisný předpony, které označují typ prostředku nebo objektů, které představují. Tyto předpony popisný začínat identifikátor kombinaci textu Třídy knihovny MFC (Microsoft Foundation) používá konvence pojmenování symbol je znázorněno v následující tabulce.

|Kategorie|Předpona|Použití|
|--------------|------------|---------|
|Prostředky|IDR_ IDD_ IDC_ IDI_ IDB_|Akcelerátoru nebo nabídky (a související nebo vlastní prostředky) dialogové okno ikony rastrového obrázku kurzoru|
|Položky nabídky|ID_|Položka nabídky|
|Příkazy|ID_|Příkaz|
|Ovládací prvky a podřízená okna|IDC_|Ovládací prvek|
|Řetězce|IDS_|Řetězec do tabulky řetězců|
|MFC|AFX_|Vyhrazeno pro předdefinované symboly MFC|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Změna symbolu nebo názvu symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)<br/>
[Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)