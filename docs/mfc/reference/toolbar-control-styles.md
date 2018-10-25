---
title: ToolBar – styly ovládacího prvku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882111e400b613c830bb45cafd03ace99c09a0c2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054933"
---
# <a name="toolbar-control-styles"></a>ToolBar – styly ovládacích prvků

[Cmfctoolbarbutton – třída](../../mfc/reference/cmfctoolbarbutton-class.md) má sadu styl příznaky, které určují vzhled a chování tlačítka. Kombinace těchto příznaků můžete nastavit voláním [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Toto téma obsahuje hodnoty příznak stylu a jejich význam.

## <a name="property-values"></a>Hodnoty vlastností

Typ tlačítka, které představuje ovládací prvek určete následující hodnoty:

|||
|-|-|
|TBBS_BUTTON|Pushbutton standardní (výchozí).  |
|TBBS_CHECKBOX|Zaškrtávací políčko.  |
|TBBS_CHECKGROUP|Začátek skupiny zaškrtávacích políček.  |
|TBBS_GROUP|Počáteční skupina tlačítek.  |
|TBBS_SEPARATOR|Oddělovač.  |

Následující hodnoty představují aktuální stav ovládacího prvku:

|||
|-|-|
|TBBS_CHECKED|Zaškrtávací políčko zaškrtnuto.  |
|TBBS_DISABLED|Ovládací prvek je zakázaný.  |
|TBBS_INDETERMINATE|Zaškrtávací políčko je v neurčitém stavu.  |
|TBBS_PRESSED|Stisknutí tlačítka.  |

Následující hodnota změní rozvržení tlačítko na panelu nástrojů:

|||
|-|-|
|TBBS_BREAK|Umístí položku na nový řádek nebo v novém sloupci bez oddělení sloupců.  |

## <a name="remarks"></a>Poznámky

Aktuální styl je uložen v [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Nenastavujte novou hodnotu `m_nStyle` přímo, protože některé odvozené třídy provést další zpracování při volání `SetStyles`.

Správce vzhledu určuje vzhled tlačítek v jednotlivých stavech. Zobrazit [správce vizualizace](../../mfc/visualization-manager.md) Další informace.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarbutton.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Správce vizualizace](../../mfc/visualization-manager.md)

