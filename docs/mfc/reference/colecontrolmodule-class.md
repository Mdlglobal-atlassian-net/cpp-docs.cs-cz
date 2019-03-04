---
title: COleControlModule Class
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: 42239ff060d5e081f273ce9dd7d87d1dbbeca716
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302153"
---
# <a name="colecontrolmodule-class"></a>COleControlModule Class

Základní třída, ze které odvozujete objekt ovládacího prvku modulu OLE.

## <a name="syntax"></a>Syntaxe

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Poznámky

Tato třída poskytuje členské funkce pro inicializaci modulu ovládacího prvku. Každý modul ovládacího prvku OLE, který používá tříd Microsoft Foundation classes může obsahovat pouze jeden objekt odvozený od `COleControlModule`. Tento objekt je vytvořen při další C++ globální objekty jsou vytvořeny. Deklarovat vaší odvozené `COleControlModule` objektu na globální úrovni.

Další informace o používání `COleControlModule` najdete v tématu [CWinApp](../../mfc/reference/cwinapp-class.md) třídy a v článku [ovládací prvky ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxctl.h

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
