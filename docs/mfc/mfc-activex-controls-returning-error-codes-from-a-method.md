---
title: "Ovládací prvky MFC ActiveX: Vrácení chybových kódů z metody | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- SetNotSupported method, using
- errors [MFC], ActiveX control error codes
- GetNotSupported method [MFC]
- FireError method [MFC]
- SCODE, MFC ActiveX controls
- ThrowError method [MFC]
ms.assetid: 771fb9c9-2413-4dcc-b386-7bc4c4adeafd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 878d31d779d6722f25e9a3b53847cea25daac6e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-returning-error-codes-from-a-method"></a>MFC –ovládací prvky ActiveX: Vrácení chybových kódů z metody
Tento článek popisuje způsob vrácení kódů chyb z metody ovládacího prvku ActiveX.  
  
 K označení, že došlo k chybě v rámci metodu, měli byste použít [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror) členská funkce, který přebírá `SCODE` (kód stavu) jako parametr. Můžete použít i předdefinovanou `SCODE` nebo definovat vlastní.  
  
> [!NOTE]
>  `ThrowError`měl by být použit pouze jako způsob vrátila chybu z v rámci Get vlastnost nebo sadu funkce nebo automation metoda. Toto jsou jediné pokusů, které obslužná rutina příslušné výjimky bude k dispozici v zásobníku.  
  
 Podpůrné funkce pro nejběžnější předdefinované neexistují `SCODE`s, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
 Seznam předdefinovaných `SCODE`s a pokyny k definování vlastní `SCODE`s, najdete v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.  
  
 Další informace o vytváření sestav výjimky v jiných oblastech kódu najdete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX: Advanced témata.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)

