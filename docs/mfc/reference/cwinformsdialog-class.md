---
title: Třída CWinFormsDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fe7c8518366065e93360187247cbd07df42d79f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122494"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog – třída
Obálka pro třídy dialogového okna knihovny MFC, který je hostitelem uživatelského ovládacího prvku Windows Forms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>Parametry  
 `TManagedControl`  
 Řízení uživatelských rozhraní .NET Framework, který se má zobrazit v aplikaci MFC.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Vytvoří `CWinFormsDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|Získá odkaz na uživatelský ovládací prvek Windows Forms.|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|V dialogovém okně knihovny MFC inicializuje pomocí vytvoření a hostování uživatelského ovládacího prvku Windows Forms v něm.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Nahradí [CWinFormsDialog::GetControl](#getcontrol) ve výrazech.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Vrhá typu jako odkaz na uživatelský ovládací prvek Windows Forms.|  
  
## <a name="remarks"></a>Poznámky  
 `CWinFormsDialog` představuje obálku pro třídu dialogové okno knihovny MFC ( [CDialog](../../mfc/reference/cdialog-class.md)), který hostuje uživatelského ovládacího prvku Windows Forms. To umožňuje zobrazení ovládacích prvků modální nebo nemodálním dialogovém okně knihovny MFC rozhraní .NET Framework.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) a [hostitelské poskytování uživatelského Windows Form jako dialogového okna knihovny MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 Vytvoří `CWinFormsDialog` objektu.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>Parametry  
 *nIDTemplate*  
 Obsahuje ID prostředku šablony dialogové okno pole. Použití editoru dialogových oken k vytvoření šablony dialogového okna a jeho uložení v souboru skriptu prostředků aplikace. Další informace o dialogovém okně šablony najdete v tématu [CDialog – třída](../../mfc/reference/cdialog-class.md).  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 Získá odkaz na uživatelský ovládací prvek Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na ovládacího prvku Windows Forms v dialogovém okně knihovny MFC.  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 Načte popisovač okna do uživatelského ovládacího prvku Windows Forms.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač okna do uživatelského ovládacího prvku Windows Forms.  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 V dialogovém okně knihovny MFC inicializuje pomocí vytvoření a hostování uživatelského ovládacího prvku Windows Forms v něm.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Logická hodnota, která určuje, zda má být z aplikace nastavte na některou z ovládacích prvků zaměření pro vstup v dialogovém okně. Pokud `OnInitDialog` vrátí nenulovou, Windows nastaví zaměření pro vstup na první ovládací prvek v dialogovém okně. Tato metoda může vrátit 0, pouze v případě, že aplikace má v dialogovém okně explicitně nastavit zaměření pro vstup na jednu z ovládacích prvků.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření dialogového okna knihovny MFC (pomocí [vytvořit](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), nebo [DoModal](../../mfc/reference/cdialog-class.md#domodal) metoda zděděno z [CDialog](../../mfc/reference/cdialog-class.md)), WM_ Odeslání zprávy INITDIALOG a tato metoda je volána. Vytvoří instanci ovládacího prvku Windows Forms v dialogovém okně a upraví velikost dialogových oken, aby dokázala pojmout velikost uživatelského ovládacího prvku. Potom hostuje nový ovládací prvek v dialogovém okně knihovny MFC.  
  
 Funkci člena přepište, pokud je třeba provést zvláštní zpracování při inicializaci dialogové okno. Další informace o použití této metody naleznete v části [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 Nahradí [CWinFormsDialog::GetControl](#getcontrol) ve výrazech.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor poskytuje pohodlné syntaxe, který nahrazuje `GetControl` ve výrazech.  
  
 Informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 Vrhá typu jako odkaz na uživatelský ovládací prvek Windows Forms.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor vrhá typu jako odkaz na ovládacího prvku Windows Forms. Slouží k předávání `CWinFormsDialog<TManagedControl>` dialogové okno na funkce, které přijímají ukazatel na objekt ovládacího prvku Windows Forms uživatele.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
