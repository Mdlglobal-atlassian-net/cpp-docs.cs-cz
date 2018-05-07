---
title: 'TN023: Standardní prostředky MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.resources
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61d6520aef1ec04c6419fb1c9c901475c9c109f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Standardní prostředky MFC
Tato poznámka popisuje standardní prostředky k dispozici s a vyžaduje knihovny MFC.  
  
## <a name="standard-resources"></a>Standardní prostředky aplikace  
 Nabízí dvě kategorie předdefinované prostředky, které můžete použít v aplikaci MFC: klip nejaktuálnější prostředky a prostředky standardní architektury.  
  
 Klip nejaktuálnější prostředky jsou další prostředky, které rozhraní není závislá na, ale které chcete přidat do vaší aplikace uživatelské rozhraní. V následujících zdrojích informací klip obrázky jsou obsaženy v ukázce MFC Obecné [CLIPART](../visual-cpp-samples.md):  
  
-   Common.rc: Jeden soubor prostředků, který obsahuje:  
  
    -   Velké kolekce ikony, které představují celou řadu obchodních a zpracování dat úlohy.  
  
    -   Několik běžných kurzory (viz také Afxres.rc).  
  
    -   Panel nástrojů rastrový obrázek, který obsahuje několik tlačítka panelu nástrojů.  
  
    -   Ikona a rastrový obrázek prostředky, které jsou používány Commdlg.dll.  
  
-   Indicate.rc: Obsahuje řetězcové prostředky pro ukazatele stavu klíč stavového řádku, jako je například "CAP" pro klávesy Caps Lock.  
  
-   Prompts.rc: Obsahuje řádku nabídky řetězcové prostředky pro každý přednastaveného příkazu, jako je například "Vytvořit nový dokument" pro `ID_FILE_NEW`.  
  
-   COMMDLG.rc: Soubor kompatibilní .rc Visual C++, který obsahuje standardní šablony COMMDLG dialogu.  
  
 Standardní framework prostředky jsou zdroje s afx – definované identifikátory, které rozhraní závisí na pro interní implementace. Chcete-li změnit tyto prostředky definované afx – zřídka musíte. V takovém případě postupujte podle pokynů uvedených dále v tomto tématu.  
  
 Následující prostředky architektury jsou obsažené v adresáři MFC\INCLUDE:  
  
-   Afxres.rc: Běžné prostředky využívané třídou rozhraní.  
  
-   Afxprint.rc: Prostředky specifické pro tisk.  
  
-   Afxolecl.rc: Specifické pro klientské aplikace OLE prostředky.  
  
-   Afxolev.rc: Specifické prostředky pro úplné aplikace serveru OLE.  
  
## <a name="using-clip-art-resources"></a>Pomocí klip nejaktuálnější prostředky  
  
#### <a name="to-use-a-clip-art-binary-resource"></a>Použití binárního prostředku klip obrázky  
  
1.  Otevřete soubor prostředků aplikace v jazyce Visual C++.  
  
2.  Otevřete Common.rc. Tento soubor obsahuje všechny binární klip nejaktuálnější prostředky. Protože soubor Common.rc je zkompilovat. to může chvíli trvat.  
  
3.  Podržte klávesu CTRL a přetáhněte prostředky, které chcete použít z Common.rc do souboru prostředků aplikace.  
  
 Další prostředky klip obrázky, postupujte podle stejných kroků. Jediným rozdílem je, že spustíte odpovídající soubor místo Common.rc.  
  
> [!NOTE]
>  Dejte pozor, abyste přesunout prostředky z Common.rc neúmyslně trvale. Podržíte klávesu CTRL a přetáhněte prostředky, se vytvoří kopie. Pokud není podržte klávesu CTRL a přetažení, přesunou se prostředky. Pokud máte obavy, že může omylem provedené změny do souboru Common.rc, klikněte na tlačítko "Ne", když budete dotázáni, zda chcete uložit změny do Common.rc.  
  
> [!NOTE]
>  Soubory .rc prostředků mít speciální `TEXTINCLUDE` prostředek v nich, který zabrání v uložení omylem nad soubory standardní .rc.  
  
### <a name="customizing-standard-framework-resources"></a>Přizpůsobení prostředky standardní architektury  
 Prostředky standardní architektury jsou obvykle součástí aplikace pomocí #include příkaz do souboru prostředků aplikace. Objekty AppWizard vygeneruje soubor prostředků. Tento soubor obsahuje prostředky odpovídající standardní architektury, v závislosti na tom, které objekty AppWizard možnosti vyberete. Můžete zkontrolovat, přidat nebo odebrat prostředky, ke kterým jsou zahrnuty změnou direktivy kompilaci. Chcete-li to provést, otevřete **prostředků** nabídku a vyberte **nastavit zahrnuje**. Podívejte se na položku upravit "Kompilaci direktivy". Příklad:  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 V případě nejběžnějších přizpůsobení prostředky standardní architektury je přidání nebo odebrání dalších zahrnuje pro tisk, klient OLE a podpora OLE serveru.  
  
 Ve výjimečných případech můžete chtít přizpůsobit obsah prostředky standardní architektury pro konkrétní aplikaci ne jenom přidávat a odebírat celý soubor. Tady kroky ukazují, jak můžete omezit prostředky, které jsou zahrnuty:  
  
##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Chcete-li přizpůsobit obsah souboru standardní prostředků  
  
1.  Otevřete soubor prostředků v jazyce Visual C++.  
  
2.  Pomocí příkazu nastavte prostředek zahrnuje odebrat `#include` pro standardní .rc soubor, který chcete přizpůsobit. Například k přizpůsobení panelu nástrojů náhledu, odebrat `#include "afxprint.rc"` řádku.  
  
3.  Otevření souborů odpovídající standardní prostředky v MFC\INCLUDE. V následujícím příkladu výše v tomto tématu příslušný soubor je MFC\Include\Aafxprint.rc  
  
4.  Zkopírujte všechny prostředky ze souboru standardní .rc do souboru prostředků aplikace.  
  
5.  Upravte kopii standardní prostředky ve vašem souboru prostředků aplikace.  
  
> [!NOTE]
>  Neměňte prostředky přímo ve standardní .rc soubory. Díky tomu bude upravit dostupné v každé aplikaci, ne jenom při je ta, kterou právě pracujete na prostředky.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

