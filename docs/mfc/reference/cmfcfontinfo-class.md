---
title: "Třída CMFCFontInfo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d0ea0572667ef45264fd52934cd2d4ee750a6d4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo – třída
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
|[CMFCFontInfo::GetFullName](#getfullname)|Načte zřetězených názvy písmo a jeho znak nastavit (skript).|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|Hodnota, která určuje znakovou sadu (skript) přidružené k písmo.|  
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Hodnota, která určuje výšku a řadu písmo.|  
|[CMFCFontInfo::m_nType](#m_ntype)|Hodnota, která určuje typ písma.|  
|[CMFCFontInfo::m_strName](#m_strname)|Název písma; například **Arial**.|  
|[CMFCFontInfo::m_strScript](#m_strscript)|Název znakovou sadu (skript) přidružené k písmo.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete připojit `CMFCFontInfo` objekt, který chcete položky [CMFCToolBarFontComboBox třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md) třída. Volání [CMFCToolBarFontComboBox::GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) metoda pro načtení ukazatel na `CMFCFontInfo` objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat různé členy `CMFCFontInfo` třídy. Příklad ukazuje, jak získat `CMFCFontInfo` objektu z `CMFCRibbonFontComboBox`a jak získat přístup k jeho místní proměnné. Tato ukázka je součástí [MSOffice 2007 Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbarfontcombobox.h  
  
##  <a name="cmfcfontinfo"></a>CMFCFontInfo::CMFCFontInfo  
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
 [v]`lpszName`  
 Název písma. Další informace najdete v tématu `lfFaceName` členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [v]`lpszScript`  
 Název skriptu (znaková sada) písma.  
  
 [v]`nCharSet`  
 Hodnota, která určuje znakovou sadu (skript) písma. Další informace najdete v tématu `lfCharSet` členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [v]`nPitchAndFamily`  
 Hodnota, která určuje výšku a řadu písmo. Další informace najdete v tématu `lfPitchAndFamily` členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktury.  
  
 [v]`nType`  
 Hodnota, která určuje typ písma. Tento parametr může být bitovou kombinaci (nebo) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.  
  
 [v]`src`  
 Existující `CMFCFontInfo` objektu, jejíž členové jsou používány k vytváření to `CMFCFontInfo` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Tato dokumentace používá podmínky *znaková sada* a *skriptu* zcela zaměnitelným významem. A *skriptu*, což je také označován jako písmo, je kolekce znaky a pravidla pro zápis těchto znaků v jeden nebo více jazyků. Kolekce znaků zahrnuje abecedy a interpunkce použít ve skriptu. Například latince slouží pro angličtinu, jako je používaný ve Spojených státech amerických a jeho abecedy obsahuje znaky a až Z. `lfCharSet` Členem [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037) struktura Určuje znakovou sadu. Například hodnota `ANSI_CHARSET` Určuje [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] znaková sada, která zahrnuje abecedy latince.  
  
##  <a name="getfullname"></a>CMFCFontInfo::GetFullName  
 Načte zřetězených názvy písmo a jeho znak nastavit (skript).  
  
```  
CString GetFullName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Řetězec, který obsahuje název písma a skript.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete získat úplný název písma. Například pokud je název písma je `Arial` a je skript písma `Cyrillic`, tato metoda vrátí hodnotu "Arial (cyrilice)".  
  
##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet  
 Hodnota, která určuje znakovou sadu (skript) přidružené k písmo.  
  
```  
const BYTE m_nCharSet;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu `nCharSet` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktor.  
  
##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily  
 Hodnota, která určuje výšku (velikost bodu) a (například serif, sans-serif a neproporcionální) řadu písmo.  
  
```  
const BYTE m_nPitchAndFamily;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu `nPitchAndFamily` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktor.  
  
##  <a name="m_ntype"></a>CMFCFontInfo::m_nType  
 Hodnota, která určuje typ písma.  
  
```  
const int m_nType;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu `nType` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktor.  
  
##  <a name="m_strname"></a>CMFCFontInfo::m_strName  
 Název písma: například **Arial**.  
  
```  
const CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu `lpszName` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktor.  
  
##  <a name="m_strscript"></a>CMFCFontInfo::m_strScript  
 Název znakovou sadu (skript) přidružené k písmo.  
  
```  
const CString m_strScript;  
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu `lpszScript` parametr [CMFCFontInfo::CMFCFontInfo](#cmfcfontinfo) konstruktor.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox – třída](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
