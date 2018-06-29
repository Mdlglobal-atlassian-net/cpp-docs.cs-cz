---
title: Třída CSettingsStoreSP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d9b7cdc0d75ec207e3bd8141ac3a0f9c5ce1d3eb
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078696"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP – třída
`CSettingsStoreSP` Třída je pomocná třída, která můžete použít k vytvoření instance [CSettingsStore třída](../../mfc/reference/csettingsstore-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Vytvoří `CSettingsStoreSP` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|Vytvoří instanci třídy, která je odvozena z `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Nastaví třídu modulu runtime. `Create` Metoda používá třídu runtime určení jaké třídy objektů, které chcete vytvořit.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|`m_dwUserData`|Vlastní uživatelská data, která je uložená v `CSettingsStoreSP` objektu. Zadáte-li tato data v konstruktoru `CSettingsStoreSP` objektu.|  
|`m_pRegistry`|`CSettingsStore`-Odvozené objektu, který `Create` metoda vytvoří.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `CSettingsStoreSP` třída pro všechny operace s registrem MFC přesměrovat do jiných umístění, jako je soubor XML nebo databázi. Postupujte přitom takto:  
  
1.  Vytvořte třídu (například `CMyStore`) a odvodí z `CSettingsStore`.  
  
2.  Použití [DECLARE_DYNCREATE –](run-time-object-model-services.md#declare_dyncreate) a [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) makra se vaše vlastní `CSettingsStore` třídy můžete povolit dynamické vytváření.  
  
3.  Přepsat virtuální funkce a implementovat `Read` a `Write` funkce ve vaší vlastní třídy. Implementujte další funkce pro čtení a zápisu dat do požadovaného umístění.  
  
4.  V aplikaci, volání `CSettingsStoreSP::SetRuntimeClass` a předat ukazatel na [CRuntimeClass struktura](../../mfc/reference/cruntimeclass-structure.md) získané z vaší třídy.  
  
 Kdykoliv rámci by obvykle přístup do registru, bude nyní dynamicky vytvořit instanci vaše vlastní třídy a použít jej číst nebo zapisovat data.  
  
 `CSettingsStoreSP::SetRuntimeClass` využívá globální statické proměnné. Pouze jeden vlastní úložiště je tedy k dispozici v čase.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsettingsstore.h  
  
##  <a name="create"></a>  CSettingsStoreSP::Create  
 Vytvoří novou instanci objektu, který je odvozený od [CSettingsStore třída](../../mfc/reference/csettingsstore-class.md).  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bAdmin*  
 Logický parametr, který určuje, zda `CSettingsStore` objekt se vytvoří v režimu správce.  
  
 [v] *bReadOnly*  
 Logický parametr, který určuje, zda `CSettingsStore` objekt se vytvoří pro přístup jen pro čtení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na nově vytvořený `CSettingsStore` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít metodu [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) určit, jaký druh objektu `CSettingsStoreSP::Create` vytvoří. Ve výchozím nastavení, tato metoda vytvoří `CSettingsStore` objektu.  
  
 Pokud vytvoříte `CSettingsStore` objektů v režimu správce, HKEY_LOCAL_MACHINE je výchozím umístěním pro všechny přístup k registru. Jinak je výchozím umístěním pro všechny přístup k registru HKEY_CURRENT_USER.  
  
 Pokud *bAdmin* je `TRUE`, aplikace musí mít administrativní oprávnění. Jinak dojde při pokusu o přístup k registru.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `Create` metodu `CSettingsStoreSP` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP  
 Vytvoří [CSettingsStoreSP třída](../../mfc/reference/csettingsstoresp-class.md) objektu.  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *dwUserData*  
 Uživatelem definované datové, `CSettingsStoreSP` objektu úložiště.  
  
### <a name="remarks"></a>Poznámky  
 `CSettingsStoreSP` Objekt ukládá data z *dwUserData* v proměnné chráněného člena `m_dwUserData`.  
  
##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass  
 Nastaví třídu modulu runtime. Metoda [CSettingsStoreSP::Create](#create) používá runtime třídu k určení typu objektu k vytvoření.  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pRTI*  
 Ukazatel na informace o běhu programu třída pro třídy odvozené od [CSettingsStore třída](../../mfc/reference/csettingsstore-class.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` v případě úspěšného; `FALSE` Pokud třída identifikovaný *pRTI* není odvozen od `CSettingsStore`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete použít [CSettingsStoreSP třída](../../mfc/reference/csettingsstoresp-class.md) odvozovat z `CSettingsStore`. Pomocí této metody `SetRuntimeClass` Pokud budete chtít vytvořit objekty vlastní třídy, který je odvozený od `CSettingsStore`.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CSettingsStore – třída](../../mfc/reference/csettingsstore-class.md)
