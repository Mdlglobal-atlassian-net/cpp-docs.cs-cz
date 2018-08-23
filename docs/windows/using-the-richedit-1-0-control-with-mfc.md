---
title: Použití ovládacího prvku RichEdit 1.0 s MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 459815b29ec8caff42d4f9a892b468dff3bf7832
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607048"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Použití ovládacího prvku RichEdit 1.0 s MFC

Použití ovládacího prvku RichEdit, nejprve je třeba volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo se telefonicky [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší ovládacího prvku RichEdit 1.0 (RICHED32. KNIHOVNY DLL).

Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třída s atributem starší ovládacího prvku RichEdit 1.0, ale `CRichEditCtrl` je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Většina metod bude fungovat, protože jsou velmi podobné RichEdit 1.0 a RichEdit 2.0, Mějte však na paměti, že existují určité rozdíly mezi 1.0 nebo 2.0 ovládací prvky, takže mohou některé metody nebudou správně fungovat nebo nepracuje vůbec.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)  
[Editor dialogových oken](../windows/dialog-editor.md)