---
title: "Třída CMultiPageDHtmlDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
dev_langs: C++
helpviewer_keywords: CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4b34d488269b47d432ffc35369725e7ca9fb7e5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog – třída
Vícestránkové dialogové okno zobrazí více stránek HTML postupně a zpracovává události z každé stránce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMultiPageDHtmlDialog : public CDHtmlDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Vytvoří objekt dialogové okno vícestránkové DHTML (Průvodce style).|  
|[CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|Zničí vícestránkové objektu dialogového okna DHTML.|  
  
## <a name="remarks"></a>Poznámky  
 Tento mechanismus tohoto postupu je [DHTML a adresy URL mapa událostí](dhtml-event-maps.md), která obsahuje vložené mapy událostí pro jednotlivé stránky.  
  
## <a name="example"></a>Příklad  
 Toto dialogové okno vícestránkové předpokládá tři HTML prostředky, které definují jednoduché průvodce jako funkce. Na první stránce `Next` tlačítko, druhý **Prev** a `Next` tlačítko a třetí **Prev** tlačítko. Při stisknutí tlačítka volá funkci obslužné rutiny [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) k načtení příslušné nové stránky.  
  
 Příslušné části deklaraci třídy (v CMyMultiPageDlg.h):  
  
 [!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]  
  
 Příslušné části v implementaci třídy (v CMyMultipageDlg.cpp):  
  
 [!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDHtmlSinkHandlerBase2`  
  
 `CDHtmlSinkHandlerBase1`  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDHtmlSinkHandler`  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDHtmlEventSink`  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)  
  
 `CMultiPageDHtmlDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdhtml.h  
  
##  <a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog  
 Vytvoří objekt dialogové okno vícestránkové DHTML (Průvodce style).  
  
```  
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,  
    LPCTSTR szHtmlResID = NULL,  
    CWnd* pParentWnd = NULL);

 
CMultiPageDHtmlDialog(
    UINT nIDTemplate,  
    UINT nHtmlResID = 0,  
    CWnd* pParentWnd = NULL);  
  
CMultiPageDHtmlDialog();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Řetězce ukončené hodnotou null, která je název prostředku šablony – dialogové okno.  
  
 `szHtmlResID`  
 Řetězce ukončené hodnotou null, která je název prostředek HTML.  
  
 `pParentWnd`  
 Ukazatel na nadřazené nebo vlastníka objektu okna (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je **NULL**, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.  
  
 `nIDTemplate`  
 Obsahuje počet ID prostředku šablony – dialogové okno.  
  
 `nHtmlResID`  
 Obsahuje počet ID prostředek HTML.  
  
##  <a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog:: ~ CMultiPageDHtmlDialog  
 Zničí vícestránkové objektu dialogového okna DHTML.  
  
```  
virtual ~CMultiPageDHtmlDialog();
```  
  
## <a name="see-also"></a>Viz také  
 [CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md)
