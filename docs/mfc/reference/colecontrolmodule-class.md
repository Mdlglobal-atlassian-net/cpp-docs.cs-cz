---
title: COleControlModule – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83c7e9bc265870e6099c231f8e15ec5e37902c55
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069292"
---
# <a name="colecontrolmodule-class"></a>COleControlModule – třída

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

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)

