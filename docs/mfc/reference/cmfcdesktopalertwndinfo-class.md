---
title: Třída CMFCDesktopAlertWndInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb682236f41294b7d14f5950ed7906832dd7d8a2
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038087"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo – třída
`CMFCDesktopAlertWndInfo` Třída se používá s [CMFCDesktopAlertWnd třída](../../mfc/reference/cmfcdesktopalertwnd-class.md). Určuje ovládacích prvků, které se zobrazí, pokud se objeví okně upozornění na ploše.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Popisovač pro ikonu, která se zobrazí.|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|ID příkazu, která je spojená s odkazem na okně upozornění na ploše.|  
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Text, který se zobrazí v okně upozornění na ploše.|  
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Odkaz, který se zobrazí v okně upozornění na ploše.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCDesktopAlertWndInfo` Třída je předán [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metoda k určení prvky, které se zobrazí na výchozí dialogovém okně upozornění na ploše. Dialogové okno výchozí může obsahovat tři položky:  
  
-   Ikonu, která je nastavená voláním [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).  
  
-   Popisek nebo textovou zprávu, která je nastavená voláním [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).  
  
-   Odkaz, který je nastaven voláním [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Chcete-li nastavit příkaz, který se spustí, až po kliknutí na odkaz, volejte [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).  
  
 Pokud výchozí dialogové okno nestačí, můžete vytvořit vlastní dialogové okno a předejte ji do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metody místo použití této třídy. Další informace najdete v tématu [CMFCDesktopAlertDialog třída](../../mfc/reference/cmfcdesktopalertdialog-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat různé členy v `CMFCDesktopAlertWndInfo` třídy. Příklad ukazuje, jak nastavit popisovač na ikonu, která se zobrazí, text, který se zobrazí v okně upozornění na ploše, na odkaz, který se zobrazí v okně upozornění na ploše a ID příkazu, která souvisí s odkazem na okně upozornění na ploše. Tato ukázka je součástí [plochy výstrahy Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxDesktopAlertDialog.h  
  
##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *src*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon  
 Popisovač pro ikonu, která se zobrazí.  
  
```  
HICON m_hIcon;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID  
 ID příkazu, která je spojená s odkazem na okně upozornění na ploše.  
  
```  
UINT m_nURLCmdID;  
```  
  
### <a name="remarks"></a>Poznámky  
 ID příkazu je odeslána vlastníkovi automaticky otevíraném okně, když uživatel klikne na odkaz určeného [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).  
  
##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText  
 Text, který se zobrazí v okně upozornění na ploše.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL  
 Odkaz, který se zobrazí v okně upozornění na ploše.  
  
```  
CString m_strURL;  
```  
  
### <a name="remarks"></a>Poznámky  
 Když uživatel klikne na odkaz, příkazu, který má [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) ID příkazu, který odešle vlastníkovi překryvné okno.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd – třída](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)   
 [CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)
