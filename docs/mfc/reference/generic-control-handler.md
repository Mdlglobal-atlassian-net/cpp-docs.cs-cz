---
title: Obecná obslužná rutina ovládacího prvku
ms.date: 11/04/2016
helpviewer_keywords:
- handlers [MFC], ON_CONTROL
- handlers [MFC]
- GenericControl Handler [MFC]
- ON_CONTROL macro [MFC]
ms.assetid: 1e25e583-5d5a-4363-8904-839991a8570d
ms.openlocfilehash: 350c0337b0b43018000c4be318821cc97cdf07c0
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612166"
---
# <a name="generic-control-handler"></a>Obecná obslužná rutina ovládacího prvku

Následující položku mapování odpovídá k rychlému vytvoření prototypu funkce.

|Položka mapování|Prototyp funkce|
|---------------|------------------------|
|ON_CONTROL ( \<funkci wNotifyCode >, \<id >, \<memberFxn >)|afx_msg void memberFxn ();|

## <a name="see-also"></a>Viz také:

[Mapy zpráv](../../mfc/reference/message-maps-mfc.md)
