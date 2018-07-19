---
title: Cmfcfontinfo – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
dev_langs:
- C++
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23ff2d857938881f1c3d9f02a1d8465a5a4e97c7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852416"
---
# <a name="cmfcfontinfo-class"></a>Cmfcfontinfo – třída
`CMFCFontInfo` Třída popisuje název a další atributy písma.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCFontInfo`|Vytvoří `CMFCFontInfo` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFontInfo::GetFullName](#getfullname)|Načte nastavení zřetězených názvy písmo a jeho znak (skript).|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Hodnota, která určuje znakovou sadu (skript) přidružené k písma.|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Hodnota, která určuje rozteč a rodiny písma.|  
|[CMFCFontInfo::m_nType](#m_ntype)|Hodnota, která určuje typ písma.|  
|[CMFCFontInfo::m_strName](#m_strname)|Název písma; například **Arial**.|  
|[CMFCFontInfo::m_strScript](#m_strscript)|Název znakovou sadu (skript) přidružené k písma.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete připojit `CMFCFontInfo` objekt položka [cmfctoolbarfontcombobox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md) třídy. Volání [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metodu pro načtení ukazatel `CMFCFontInfo` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak využívat různé členy `CMFCFontInfo` třídy. Tento příklad ukazuje, jak získat `CMFCFontInfo` objektu z `CMFCRibbonFontComboBox`a jak přistupovat ke své místní proměnné. V tomto příkladu je součástí [MSOffice 2007 demonstrační ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo  
 Vytvoří `CMFCFontInfo` objektu.  
  
```  
CMFCFontInfo(
    LPCTSTR lpszName,  
    LPCTSTR lpszScript,  
    BYTE nCharSet,  
    BYTE nPitchAndFamily,  
    int nType);  
  
CMFCFontInfo(const CMFCFontInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszName*  
 Název písma. Další informace najdete v tématu `lfFaceName` člena [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] *lpszScript*  
 Název skriptu (znaková sada) písma.  
  
 [in] *nCharSet*  
 Hodnota, která určuje znakové sady (skript) písma. Další informace najdete v tématu `lfCharSet` člena [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] *nPitchAndFamily*  
 Hodnota, která určuje rozteč a rodiny písma. Další informace najdete v tématu `lfPitchAndFamily` člena [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [in] *nTyp*  
 Hodnota, která určuje typ písma. Tento parametr může být bitová kombinace (nebo) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.  
  
 [in] *src*  
 Existující `CMFCFontInfo` objekt, jehož členy se používají k vytvoření to `CMFCFontInfo` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Tato dokumentace používá podmínky *znaková sada* a *skript* Zaměnitelně. A *skript*, což je také označovaný jako systém zápisu, je kolekce znaků a pravidla pro zápis tyto znaky v jedné nebo více jazyků. Kolekce znaků obsahuje abecedy a interpunkci v tomto skriptu. Například latince slouží pro angličtinu, jako je slyšet ve Spojených státech amerických a zahrnuje jeho abecední znaky a až Z. `lfCharSet` Člena [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura Určuje znakovou sadu. Například hodnota ANSI_CHARSET Určuje, [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] znaková sada, která zahrnuje abecedy latince.  
  
##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName  
 Načte nastavení zřetězených názvy písmo a jeho znak (skript).  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje název písma a skript.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete získat úplný název písma. Například, pokud je název písma **Arial** a skript písmo **cyrilice**, tato metoda vrátí "Arial (cyrilice)".  
  
##  <a name="m_ncharset"></a>  CMFCFontInfo::m_nCharSet  
 Hodnota, která určuje znakovou sadu (skript) přidružené k písma.  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu *nCharSet* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktoru.  
  
##  <a name="m_npitchandfamily"></a>  CMFCFontInfo::m_nPitchAndFamily  
 Hodnota, která určuje rozteč (velikost) a řady (například serif, sans-serif a neproporcionální) písma.  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu *nPitchAndFamily* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktoru.  
  
##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType  
 Hodnota, která určuje typ písma.  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu *nTyp* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktoru.  
  
##  <a name="m_strname"></a>  CMFCFontInfo::m_strName  
 Název písma: například **Arial**.  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu *lpszName* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktoru.  
  
##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript  
 Název znakovou sadu (skript) přidružené k písma.  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu *lpszScript* parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktoru.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfctoolbarfontcombobox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox – třída](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
