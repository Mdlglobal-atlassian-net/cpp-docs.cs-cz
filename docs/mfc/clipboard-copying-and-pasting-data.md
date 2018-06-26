---
title: 'Schránka: Kopírování a vkládání dat | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4756da7459f3e584dd02b882f5c790412c095561
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929465"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schránka: Kopírování a vkládání dat
Toto téma popisuje minimální práce nezbytné k implementaci pro kopírování a vkládání ze schránky v aplikaci OLE. Doporučujeme, abyste si přečetli [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) témata než budete pokračovat.  
  
 Než budete moct implementovat kopírování nebo vložením, je nutné zadat funkce pro zpracování kopírovat, vyjmout a Vložit možnosti v nabídce Upravit.  
  
##  <a name="_core_copying_or_cutting_data"></a> Kopírování nebo vyjímání Data  
  
#### <a name="to-copy-data-to-the-clipboard"></a>Zkopírujte data do schránky.  
  
1.  Zjistěte, zda data, která mají být zkopírovány nativní data nebo je vložené nebo propojené položky.  
  
    -   Pokud data vložené nebo propojené, získání ukazatele na `COleClientItem` objekt, který byl vybrán.  
  
    -   Pokud je nativní data a aplikace je server, vytvořit nový objekt odvozené z `COleServerItem` obsahující vybraná data. Jinak, vytvoření `COleDataSource` objekt pro data.  
  
2.  Volání vybranou položku `CopyToClipboard` – členská funkce.  
  
3.  Pokud se uživatel rozhodl operace vyjmutí místo operace kopírování, odstranění vybraných dat z vaší aplikace.  
  
 Příkladem tohoto pořadí najdete v sekci `OnEditCut` a `OnEditCopy` funkcí v MFC OLE ukázkové programy [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md). Všimněte si, že tyto ukázky zachovat ukazatel aktuálně vybraná data, takže krok 1 je již dokončena.  
  
##  <a name="_core_pasting_data"></a> Vkládání dat  
 Vkládání dat je složitější než kopírování, protože je třeba vybrat formát pro použití v vložení dat do vaší aplikace.  
  
#### <a name="to-paste-data-from-the-clipboard"></a>Chcete-li vložit data ze schránky  
  
1.  Ve třídě zobrazení implementovat `OnEditPaste` pro zpracování uživatelé v nabídce Upravit zvolíte možnost vložení.  
  
2.  V `OnEditPaste` fungovat, vytvořte `COleDataObject` objekt a volání jeho `AttachClipboard` členskou funkci pro tento objekt propojit data do schránky.  
  
3.  Volání `COleDataObject::IsDataAvailable` ke kontrole, jestli konkrétní formát je k dispozici.  
  
     Alternativně můžete použít `COleDataObject::BeginEnumFormats` hledání jiných formátů najděte nejvíce vhodné k vaší aplikaci.  
  
4.  Proveďte vložení formátu.  
  
 Příklad toho, jak to funguje, najdete v části implementace `OnEditPaste` členské funkce v zobrazení tříd definovaných v aplikacích MFC OLE ukázka [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md).  
  
> [!TIP]
>  Hlavní výhodou oddělení operaci vložení do vlastní funkce je, že má stejný kód vložte lze použít při přetažení dat v aplikaci během operace přetažení myší. Jako OCLIENT a HIERSVR vaše `OnDrop` funkce můžete také zavolat `DoPasteItem`, opětovné použití kódu zapsat implementace operace vkládání.  
  
 Pro zpracování Vložit jinak možnost v nabídce Upravit, naleznete v tématu [dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md).  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)  
  
-   [Objekty a data zdroje dat OLE a uniform přenosu dat](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE – přetažení](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## <a name="see-also"></a>Viz také  
 [Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

