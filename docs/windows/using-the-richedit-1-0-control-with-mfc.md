---
title: Použití ovládacího prvku RichEdit 1.0 s MFC
ms.date: 11/04/2016
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
ms.openlocfilehash: 080ad995b9c7a041337d9b296d6ef8906e7f20ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468312"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Použití ovládacího prvku RichEdit 1.0 s MFC

Použití ovládacího prvku RichEdit, nejprve je třeba volat [afxinitrichedit2 –](../mfc/reference/application-information-and-management.md#afxinitrichedit2) načíst ovládacího prvku RichEdit 2.0 (RICHED20. Knihovny DLL), nebo se telefonicky [afxinitrichedit –](../mfc/reference/application-information-and-management.md#afxinitrichedit) načíst starší ovládacího prvku RichEdit 1.0 (RICHED32. KNIHOVNY DLL).

Můžete použít aktuální [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) třída s atributem starší ovládacího prvku RichEdit 1.0, ale `CRichEditCtrl` je určen pouze pro podporu ovládacího prvku RichEdit 2.0. Většina metod bude fungovat, protože jsou velmi podobné RichEdit 1.0 a RichEdit 2.0, Mějte však na paměti, že existují určité rozdíly mezi 1.0 nebo 2.0 ovládací prvky, takže mohou některé metody nebudou správně fungovat nebo nepracuje vůbec.

## <a name="requirements"></a>Požadavky

MFC

## <a name="see-also"></a>Viz také

[Řešení potíží s editorem dialogového okna](../windows/troubleshooting-the-dialog-editor.md)<br/>
[Editor dialogových oken](../windows/dialog-editor.md)