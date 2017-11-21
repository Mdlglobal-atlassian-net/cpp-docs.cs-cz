---
title: "Vykreslování obrázků ze seznamu obrázků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf53177e0d24777a5447c6655e7b801955610168
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="drawing-images-from-an-image-list"></a>Vykreslování obrázků ze seznamu obrázků
Kreslení bitovou kopii, použijte [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) – členská funkce. Určete ukazatel na objekt kontextu zařízení, index bitové kopie k vykreslení, umístění v kontextu zařízení, kdy k vykreslení bitovou kopii a sadu jsou označeny styl vykreslování.  
  
 Pokud zadáte `ILD_TRANSPARENT` styl, **kreslení** používá ve dvou krocích k vykreslení maskované bitové kopie. Nejprve provádí logickou- a operace na službu bits bitové kopie a bits masky. Pak provede operaci logické XOR na výsledky první operace a na pozadí bits kontextu cílové zařízení. Tento proces vytvoří průhledné oblasti v výsledný obraz; To znamená každý bit bílé v masce způsobí, že odpovídající bit výsledný obrázek, který má být průhledná.  
  
 Před kreslení maskované bitové kopie na plnou barvou pozadí, měli byste použít [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) – členská funkce nastavit barvu pozadí seznamu obrázků na barvu stejný jako cíl. Nastavení barvu eliminuje potřebu vytvářet průhledné oblasti v bitové kopii a umožňuje **kreslení** jednoduše zkopírovat bitovou kopii do kontextu cílového zařízení, což vede k významnému zvýšení výkonu. Kreslení bitovou kopii, zadejte `ILD_NORMAL` stylu při volání **kreslení**.  
  
 Můžete nastavit barvu pozadí seznamu maskované obrázků ([CImageList](../mfc/reference/cimagelist-class.md)) kdykoli, takže to nevykresluje správně na všechny pevné pozadí. Nastavení barvy pozadí `CLR_NONE` způsobí, že bitové kopie, které se mají vykreslovat transparentně ve výchozím nastavení. Chcete-li načíst barvu pozadí seznamu obrázků, použijte [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) – členská funkce.  
  
 `ILD_BLEND25` a `ILD_BLEND50` styly tónování bitové kopie s barva zvýraznění systému. Tyto styly jsou užitečné, pokud použijete maskované image představují objekt, který může uživatel vybrat. Například můžete použít `ILD_BLEND50` styl kreslení bitovou kopii, když ho uživatel vybere.  
  
 Bitovou kopii nonmasked se zkopíruje na cílovém zařízení kontext pomocí **SRCCOPY** rastrové operace. Barvy v bitové kopii se zobrazí stejný bez ohledu na barvu pozadí kontextu zařízení. Kreslení styly definované v **kreslení** také mít žádný vliv na vzhled nonmasked bitové kopie.  
  
 Kromě členská funkce kreslení jinou funkci [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozšiřuje možnosti vykreslování obrázku. `DrawIndirect`přijímá jako parametr, [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury. Tato struktura slouží k přizpůsobení vykreslování aktuální image, včetně použití kódů rastrové operace (ROP). Další informace o kódy ROP najdete v tématu [rastrové operace kódy](http://msdn.microsoft.com/library/windows/desktop/dd162892) a [bitmap jako štětce](http://msdn.microsoft.com/library/windows/desktop/dd183378) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CImageList](../mfc/using-cimagelist.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

