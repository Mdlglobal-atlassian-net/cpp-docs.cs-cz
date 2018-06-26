---
title: 'Ovládací prvky MFC ActiveX: Vrácení chybových kódů z metody | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdcd18a80b430a0a8576effaaa46215dd5eb9600
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36927916"
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody
Tento článek popisuje způsob vrácení kódů chyb z metody ovládacího prvku ActiveX.  
  
 K označení, že došlo k chybě v rámci metodu, měli byste použít [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) členská funkce, která přebírá kód SCODE (kód stavu) jako parametr. Můžete použít předdefinované kód SCODE nebo definovat vlastní.  
  
> [!NOTE]
>  `ThrowError` měl by být použit pouze jako způsob vrátila chybu z v rámci Get vlastnost nebo sadu funkce nebo automation metoda. Toto jsou jediné pokusů, které obslužná rutina příslušné výjimky bude k dispozici v zásobníku.  
  
 Podpůrné funkce neexistuje, nejběžnější předdefinované SCODEs, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Seznam předdefinovaných SCODEs a pokyny k definování vlastní SCODEs, najdete v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.  
  
 Další informace o vytváření sestav výjimky v jiných oblastech kódu najdete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

