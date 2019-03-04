---
title: 'TN023: Standardní prostředky MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.resources
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: b4edc00f77152b8d677f3113e0ed6386569b0988
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277674"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Standardní prostředky MFC

Tato poznámka popisuje standardní prostředky aplikace součástí a vyžadované knihovnou MFC.

## <a name="standard-resources"></a>Standardní prostředky aplikace

Nabízí dvě kategorie předdefinované prostředky, které můžete použít v aplikaci knihovny MFC: klipart prostředky a standardních prostředcích rozhraní.

Klipart prostředky jsou další prostředky, které nezávisí na rozhraní, ale které můžete chtít přidat do vaší aplikace uživatelského rozhraní. Následující prostředky klipart jsou obsaženy v ukázce MFC Obecné [klipart](../visual-cpp-samples.md):

- Common.rc: Jeden soubor prostředků, který obsahuje:

   - Rozsáhlá kolekce ikon, které představují širokou škálu obchodních a zpracování dat úlohy.

   - Několik běžných kurzory (viz také Afxres.rc).

   - Rastrový obrázek panelu nástrojů, který obsahuje několik tlačítek panelu nástrojů.

   - Ikona rastrového obrázku a prostředky, které jsou používány Commdlg.dll.

- Indicate.rc: Obsahuje prostředky řetězců pro indikátory stavu klíče stavového řádku, jako je například "Limit" pro Caps Lock.

- Prompts.rc: Id_file_new – obsahuje řádku nabídky řetězcové prostředky pro každou přednastaveného příkazu, jako je například "Vytvořit nový dokument".

- COMMDLG.rc: Soubor .rc kompatibilní Visual C++, který obsahuje standardní šablony COMMDLG dialogového okna.

Standardních prostředcích rozhraní jsou prostředky s afx – definované identifikátory, které rozhraní závisí na interní implementace. Zřídka bude nutné změnit tyto afx – definované prostředky. Pokud tak učiníte, postupujte podle pokynů uvedených dále v tomto tématu.

Následující prostředky architektury jsou obsaženy v adresáři MFC\INCLUDE:

- Afxres.rc: Běžné prostředky využívané třídou rozhraní framework.

- Afxprint.rc: Prostředky specifické pro tisk.

- Afxolecl.rc: Prostředky specifické pro OLE klientské aplikace.

- Afxolev.rc: Prostředky specifické pro úplné aplikace serveru OLE.

## <a name="using-clip-art-resources"></a>Použití prostředků klipart

#### <a name="to-use-a-clip-art-binary-resource"></a>Použít na binární prostředek klipart

1. Otevřete soubor prostředků vaší aplikace v jazyce Visual C++.

1. Open Common.rc. Tento soubor obsahuje všechny binární klipart prostředky. Protože Common.rc soubor je zkompilován. to může chvíli trvat.

1. Podržte klávesu CTRL při přetahování prostředky, které chcete použít z Common.rc do souboru prostředků vaší aplikace.

Další prostředky klipart, postupujte podle stejných kroků. Jediným rozdílem je, že otevřete soubor .rc příslušné místo Common.rc.

> [!NOTE]
>  Dejte pozor, abyste přesunout prostředky z Common.rc neúmyslně trvale. Pokud podržíte klávesu CTRL při přetahování prostředky, vytvoří se kopie. Pokud jste není podržte CTRL při přetahování, přesunou se prostředky. Pokud máte obavy, že může nechtěně provedli jste změny do souboru Common.rc, klikněte na "Ne", když se zobrazí výzva, jestli se má uložit změny do Common.rc.

> [!NOTE]
>  Soubory prostředků .rc mít speciálnímu prostředku TEXTINCLUDE v nich, které zabrání v uložení náhodně nad rámec standardních .rc soubory.

### <a name="customizing-standard-framework-resources"></a>Přizpůsobení standardních prostředcích rozhraní

Standardních prostředcích rozhraní jsou obvykle zahrnuta v aplikaci s použitím #include příkaz Soubor prostředků aplikace. AppWizard vygeneruje soubor prostředků. Tento soubor obsahuje odpovídající standardních prostředcích rozhraní, v závislosti na tom, jaké možnosti AppWizard vyberete. Můžete zkontrolovat, přidat nebo odebrat prostředky, které jsou zahrnuty změnou směrnice času kompilace. Chcete-li to provést, otevřete **prostředků** nabídky a vybereme **Set Includes**. Podívejte se na upravovaná položka "Směrnice času kompilace". Příklad:

```
#include "afxres.rc"
#include "afxprint.rc"
```

Přizpůsobení standardních prostředcích rozhraní nejběžnější případ je přidání nebo odebrání dalších zahrnuje pro tisk, klient OLE a podpora serveru OLE.

Ve výjimečných případech může být vhodné přizpůsobit obsah standardních prostředcích rozhraní pro konkrétní aplikaci ne jenom přidávat a odebírat celý soubor. Tady kroky ukazují, jak můžete omezit prostředky, které jsou zahrnuty:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Chcete-li přizpůsobit obsah souboru standardních prostředků

1. Otevřete soubor prostředků v jazyce Visual C++.

1. Odebrat pomocí příkazu Set Includes prostředků `#include` standardní .rc souboru, který chcete přizpůsobit. Například přizpůsobení panelu nástrojů náhledu tisku, odeberte `#include "afxprint.rc"` řádku.

1. Otevřete soubory odpovídající standardní prostředky v MFC\INCLUDE. V následujícím příkladu výše v tomto tématu je příslušný soubor MFC\Include\Aafxprint.rc

1. Zkopírujte všechny prostředky ze souboru .rc standardní do souboru prostředků aplikace.

1. Upravte kopii standardní prostředky aplikace v souboru prostředků aplikace.

> [!NOTE]
>  Neprovádějte žádné změny přímo do souborů .rc standardní prostředky. Tím se upravit prostředky, které jsou k dispozici v každé aplikaci, ne jenom v ta, kterou právě pracujete.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
