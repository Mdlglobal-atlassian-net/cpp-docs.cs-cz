---
title: "Ovládací prvky MFC ActiveX: Optimalizace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46a17a6594db6c59148042f6e8c6cc72c7068dc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-optimization"></a>MFC – ovládací prvky ActiveX: Optimalizace
Tento článek vysvětluje techniky, které můžete použít k optimalizaci vaše ovládací prvky ActiveX pro dosažení vyššího výkonu.  
  
 Témata [zapnutí vypnout aktivovat při viditelné možnost](../mfc/turning-off-the-activate-when-visible-option.md) a [poskytování myši interakce při neaktivní](../mfc/providing-mouse-interaction-while-inactive.md) popisují ovládacích prvků, které nejsou vytvoření okna do aktivace. Téma [zajištění aktivace bez oken](../mfc/providing-windowless-activation.md) popisuje ovládací prvky, které nikdy vytvoření okna, i když se aktivuje.  
  
 Windows mají dva hlavní nevýhody pro objekty OLE: brání tomu, aby objekty z transparentní nebo nepravoúhlý, když je aktivní a přidat velké nároky na vytváření instancí a zobrazení ovládacích prvků. Vytvoření okna obvykle trvá 60 procent času vytvoření ovládacího prvku. V jednom okně Sdílené (obvykle kontejneru) a některé odesílající kódu obdrží ovládacího prvku stejné okno služby, obecně bez ztráty výkonu. Okno je většinou nárokům pro objekt.  
  
 Některé optimalizace zlepšení nutně výkonu při vaší ovládacího prvku v určitých kontejnerech. Například kontejnery vydané před 1996 nepodporovaly aktivace bez oken, takže implementace tato funkce nebude poskytovat výhody v kontejnerech starší. Téměř každý kontejner však podporuje trvalost, takže optimalizace trvalosti kódu ovládacího prvku se pravděpodobně zvýší jeho výkon v kontejneru. Pokud vlastní ovládací prvek je určený speciálně pro použití s jeden konkrétní typ kontejneru, můžete pro zkoumání který optimalizace nepodporuje tohoto kontejneru. Obecně platí ale, pokuste se implementují jako mnoho z těchto postupů, jak se dají použít pro vaše konkrétní řízení Ujistěte se, že vlastní ovládací prvek provádí a také ho pravděpodobně můžete v široké škály kontejnerů.  
  
 Můžete implementovat řadu tyto optimalizace prostřednictvím [Průvodce ovládacím prvkem ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md)na [nastavení řízení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky.  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Možnosti optimalizace OLE Průvodce ovládacím prvkem ActiveX knihovny MFC  
  
|Ovládací prvek nastavení Průvodce ovládacím prvkem ActiveX knihovny MFC|Akce|Další informace|  
|-------------------------------------------------------|------------|----------------------|  
|**Aktivovat při viditelné** zaškrtávací políčko|Zrušte zaškrtnutí|[Vypnutí při aktivaci Visible – možnost](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**Aktivace bez oken** zaškrtávací políčko|Vyberte|[Zajišťování aktivace bez oken](../mfc/providing-windowless-activation.md)|  
|**Neoříznutého kontextu zařízení** zaškrtávací políčko|Vyberte|[Použití neoříznutého kontextu zařízení](../mfc/using-an-unclipped-device-context.md)|  
|**Bez blikání aktivace** zaškrtávací políčko|Vyberte|[Zajištění aktivace bez blikání](../mfc/providing-flicker-free-activation.md)|  
|**Myš ukazatel oznámení o neaktivní** zaškrtávací políčko|Vyberte|[Zajištění interakce s myší v neaktivním stavu](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Optimalizované kreslení kód** zaškrtávací políčko|Vyberte|[Optimalizace vykreslování ovládacích prvků](../mfc/optimizing-control-drawing.md)|  
  
 Podrobné informace o členské funkce, které implementují tyto optimalizace najdete v tématu [COleControl](../mfc/reference/colecontrol-class.md). Členské funkce jsou uvedeny podle použití, jako například [bez oken Operations](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) a [neaktivní ukazatel zpracování funkce](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Další informace naleznete v tématu:  
  
-   [Optimalizace trvalosti a inicializace](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Zajišťování aktivace bez oken](../mfc/providing-windowless-activation.md)  
  
-   [Vypnutí při aktivaci Visible – možnost](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Zajištění interakce s myší v neaktivním stavu](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Zajištění aktivace bez blikání](../mfc/providing-flicker-free-activation.md)  
  
-   [Použití neoříznutého kontextu zařízení](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optimalizace vykreslování ovládacích prvků](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

