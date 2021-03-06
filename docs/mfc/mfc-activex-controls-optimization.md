---
title: 'MFC – ovládací prvky ActiveX: Optimalizace'
ms.date: 09/12/2018
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
ms.openlocfilehash: 08cbb5ab0ff9b8c165e549bc2b250daebc1ce177
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186889"
---
# <a name="mfc-activex-controls-optimization"></a>MFC – ovládací prvky ActiveX: Optimalizace

Tento článek popisuje postupy, které vám umožní optimalizovat vaše ovládací prvky ActiveX pro zajištění lepšího výkonu.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Témata [zapnutí vypnout the možnosti Activate When Visible](../mfc/turning-off-the-activate-when-visible-option.md) a [poskytuje myši interakce při neaktivní](../mfc/providing-mouse-interaction-while-inactive.md) diskutovat o ovládací prvky, které pro ně nevytvoříte časové období, dokud nebude aktivován. Téma [zajištění aktivace bez oken](../mfc/providing-windowless-activation.md) popisuje ovládací prvky, které nikdy vytvoření okna, i když jsou aktivované.

Windows máte dvě hlavní nevýhody pro objekty OLE: brání tomu, aby objekty z je transparentní nebo vytvoření nepravoúhlého, pokud je aktivní a přidat velké nároky na vytváření instancí a zobrazení ovládacích prvků. Vytvoření časového období trvá obvykle 60 procent společností z žebříčku čas vytvoření ovládacího prvku. Jediné sdílené okno (obvykle kontejneru) a některých dispatching kód ovládací prvek dostane stejné okno služby obvykle bez ztráty výkonu. Okno je většinou zbytečnou režii pro objekt.

Některé optimalizace nevedou k lepšímu nutně výkon při použití ovládacího prvku v určitých kontejnery. Například kontejnery vydaný před 1996 nepodporovalo aktivace bez oken, takže implementaci této funkce, nebudou zajišťovat výhoda v starší kontejnery. Téměř každý kontejner však podporuje trvalost, tak optimalizace trvalosti kódu ovládacího prvku se pravděpodobně vylepšit výkon v kontejneru. Pokud váš ovládací prvek je určený speciálně pro použití s konkrétní typu kontejneru, můžete chtít prozkoumat které z těchto optimalizacích podporuje tohoto kontejneru. Obecně platí ale doporučujeme implementovat jako mnoho z následujících postupů, jak se dají použít pro konkrétní ovládací prvek Ujistěte se, že ovládací prvek funguje stejně dobře jako to pravděpodobně v široké škály kontejnerů.

Můžete implementovat řadu těchto optimalizacích prostřednictvím [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md)na [nastavení](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Možnosti optimalizace OLE průvodce ovládací prvek ActiveX knihovny MFC

|Nastavení ovládacího prvku v Průvodci ovládací prvek ActiveX knihovny MFC|Akce|Další informace|
|-------------------------------------------------------|------------|----------------------|
|**Aktivovat, když je viditelné** zaškrtávací políčko|Vymazat|[Vypnutí aktivován, když možnost viditelná](../mfc/turning-off-the-activate-when-visible-option.md)|
|**Aktivace bez oken** zaškrtávací políčko|Vyberte|[Zajišťování aktivace bez oken](../mfc/providing-windowless-activation.md)|
|**Neoříznutého kontextu zařízení** zaškrtávací políčko|Vyberte|[Použití neoříznutého kontextu zařízení](../mfc/using-an-unclipped-device-context.md)|
|**Aktivace bez blikání** zaškrtávací políčko|Vyberte|[Zajištění aktivace bez blikání](../mfc/providing-flicker-free-activation.md)|
|**Myš ukazatel oznámení, pokud je neaktivní** zaškrtávací políčko|Vyberte|[Zajištění interakce s myší v neaktivním stavu](../mfc/providing-mouse-interaction-while-inactive.md)|
|**Optimalizované vykreslení kódu** zaškrtávací políčko|Vyberte|[Optimalizace vykreslování ovládacích prvků](../mfc/optimizing-control-drawing.md)|

Podrobné informace o členské funkce, které implementují tyto optimalizace najdete v tématu [COleControl](../mfc/reference/colecontrol-class.md).

Další informace naleznete v tématu:

- [Optimalizace trvalosti a inicializace](../mfc/optimizing-persistence-and-initialization.md)

- [Zajišťování aktivace bez oken](../mfc/providing-windowless-activation.md)

- [Vypnutí aktivován, když možnost viditelná](../mfc/turning-off-the-activate-when-visible-option.md)

- [Zajištění interakce s myší v neaktivním stavu](../mfc/providing-mouse-interaction-while-inactive.md)

- [Zajištění aktivace bez blikání](../mfc/providing-flicker-free-activation.md)

- [Použití neoříznutého kontextu zařízení](../mfc/using-an-unclipped-device-context.md)

- [Optimalizace vykreslování ovládacích prvků](../mfc/optimizing-control-drawing.md)

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
