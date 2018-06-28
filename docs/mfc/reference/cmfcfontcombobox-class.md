---
title: Třída CMFCFontComboBox | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9141dec6fdcb966dcdb664bb8dc090b50a10a614
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039996"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox – třída
`CMFCFontComboBox` Třída vytvoří prvek pole se seznamem, který obsahuje seznam písem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCFontComboBox : public CComboBox  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Vytvoří `CMFCFontComboBox` objektu.|  
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCFontComboBox::CompareItem`|Voláno rámcem určit relativní pozici novou položku do pole seřazený seznam prvku pole se seznamem aktuální písma. (Přepisuje [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|  
|`CMFCFontComboBox::DrawItem`|Voláno rámcem k vykreslení zadanou položku do aktuální ovládacího prvku pole se seznamem písma. (Přepisuje [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|  
|[CMFCFontComboBox::GetSelFont](#getselfont)|Načte informace o aktuálně vybrané písmo.|  
|`CMFCFontComboBox::MeasureItem`|Voláno rámcem k informování Windows rozměry pole se seznamem do aktuální ovládacího prvku pole se seznamem písma. (Přepisuje [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|  
|`CMFCFontComboBox::PreTranslateMessage`|Přeloží zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCFontComboBox::SelectFont](#selectfont)|Vybere písmo, který odpovídá zadaným kritériím z pole se seznamem písma.|  
|[CMFCFontComboBox::Setup](#setup)|Inicializuje seznam položek v poli se seznamem písmo.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Určuje rozhraní, které Písmo sloužící k vykreslení popisky položek v aktuální pole se seznamem písma.|  
  
## <a name="remarks"></a>Poznámky  
 Použít `CMFCFontComboBox` objektu v dialogovém okně, přidejte `CMFCFontComboBox` proměnnou třídy dialogového okna. Potom v `OnInitDialog` metoda pole třídy dialogového okna, volání [CMFCFontComboBox::Setup](#setup) metoda pro inicializaci seznam položek v ovládacím prvku pole se seznamem.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 [CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxfontcombobox.h  
  
##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox  
 Vytvoří `CMFCFontComboBox` objektu.  
  
```  
CMFCFontComboBox();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont  
 Načte informace o aktuálně vybrané písmo.  
  
```  
CMFCFontInfo* GetSelFont() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CMFCFontInfo třída](../../mfc/reference/cmfcfontinfo-class.md) objekt, který popisuje písmo. Může být `NULL` Pokud do pole se seznamem je vybrané žádné písmo.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont  
 Určuje rozhraní, které Písmo sloužící k vykreslení popisky položek v aktuální pole se seznamem písma.  
  
```  
static BOOL m_bDrawUsingFont;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` směrovat rozhraní používat stejné písmo k vykreslení každý popisek položky. Tento člen nastavit na `FALSE` směrovat rozhraní k vykreslení každý popisek položky s písma, jejíž název je stejný jako popisek. Výchozí hodnota tohoto člena je `FALSE`.  
  
##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont  
 Vybere písmo, který odpovídá zadaným kritériím z pole se seznamem písma.  
  
```  
BOOL SelectFont(CMFCFontInfo* pDesc);

 
BOOL SelectFont(
    LPCTSTR lpszName,  
    BYTE nCharSet=DEFAULT_CHARSET);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pDesc*  
 Odkazuje na objekt popis písma.  
  
 [v] *lpszName*  
 Určuje název písma.  
  
 [v] *nCharSet*  
 Určuje znakovou sadu. Výchozí hodnota je DEFAULT_CHARSET. Další informace najdete v tématu `lfCharSet` členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud položku v poli se seznamem písmo odpovídá objektu určeného písma popis nebo název písma a charset; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k výběru a přejděte na položku v poli se seznamem písmo, která odpovídá zadané písmo.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SelectFont` metoda v `CMFCFontComboBox` třídy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]  
  
##  <a name="setup"></a>  CMFCFontComboBox::Setup  
 Inicializuje seznam položek v poli se seznamem písmo.  
  
```  
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,  
    BYTE nCharSet=DEFAULT_CHARSET,  
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *nFontType*  
 Určuje typ písma. Výchozí hodnota je bitová kombinace (nebo) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.  
  
 [v] *nCharSet*  
 Určuje písmo znakovou sadu. Výchozí hodnota je DEFAULT_CHARSET.  
  
 [v] *nPitchAndFamily*  
 Určuje výšku písma a rodiny. Výchozí hodnota je DEFAULT_PITCH.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud pole se seznamem písma byl inicializován úspěšně; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda inicializuje pole se seznamem písma tak, že vytváření výčtu aktuálně instalovaných písem, které odpovídají zadané parametry a vkládání těchto názvů písem v poli se seznamem písmo.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Setup` metoda v `CMFCFontComboBox` třídy. Tato ukázka je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)
