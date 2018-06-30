---
title: Třída CWinFormsControl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ec945c5f0cdbb0c12f49b90719c31bf841ef2f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121634"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl – třída
Poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### <a name="parameters"></a>Parametry  
 `TManagedControl`  
 Prvku rozhraní .NET Framework Windows Forms, který se má zobrazit v aplikaci MFC.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Vytvoří objekt obálky knihovny MFC Windows Forms ovládací prvek.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Vytvoří ovládacího prvku Windows Forms v MFC kontejner.|  
|[CWinFormsControl::GetControl](#getcontrol)|Načte ukazatel ovládacího prvku Windows Forms.|  
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Načte popisovač do ovládacího prvku Windows Forms.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Nahradí [CWinFormsControl::GetControl](#getcontrol) ve výrazech.|  
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Vrhá typu jako ukazatel do ovládacího prvku Windows Forms.|  
  
## <a name="remarks"></a>Poznámky  
 `CWinFormsControl` Třída poskytuje základní funkce pro hostování ovládacího prvku Windows Forms.  
  
 Další informace o používání Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 MFC kód by neměl mezipaměti popisovače oken (obvykle se uloží v `m_hWnd`). Některé vlastnosti ovládacích prvků Windows Forms vyžadovat, aby základní Win32 `Window` být zrušen a znovu vytvořena pomocí `DestroyWindow` a `CreateWindow`. Obslužné rutiny implementace MFC Windows Forms `Destroy` a `Create` události ovládacích prvků k aktualizaci `m_hWnd` člen.  
  
> [!NOTE]
>  MFC Windows Forms integrace funguje jenom v projektech, které dynamicky propojit s knihovnou MFC (ve kterém je definovaný AFXDLL –).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwinforms.h  
  
##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl  
 Vytvoří ovládacího prvku Windows Forms v MFC kontejner.  
  
```  
inline BOOL CreateManagedControl(
    System::Type^ pType,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID)  
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);

 
inline BOOL CreateManagedControl(
    DWORD dwStyle,  
    int nPlaceHolderID,  
    CWnd* pParentWnd);

 
inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID);
```  
  
### <a name="parameters"></a>Parametry  
 *pType*  
 Datový typ ovládacího prvku, který se má vytvořit. Musí být [typ](https://msdn.microsoft.com/en-us/library/system.type) datového typu.  
  
 *dwStyle*  
 Styl okna, které chcete použít pro ovládací prvek. Zadejte kombinaci [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). V současné době jsou podporovány pouze následující styly: ws_tabstop –, ws_visible –, ws_disabled – a ws_group –.  
  
 *Rect –*  
 A [Rect – struktura](../../mfc/reference/rect-structure1.md) souřadnice levého a pravého dolního rozích ovládacího prvku, který definuje (nejprve přetížení pouze).  
  
 *nPlaceHolderID*  
 Popisovač řízení držitel statické místní umístěny v editoru prostředků. Nově vytvořený ovládacího prvku Windows Forms nahrazuje statické ovládací prvek, za předpokladu, že její umístění, pořadí z-order a styly (druhý přetížení pouze).  
  
 *pParentWnd*  
 Ukazatel do nadřazeného okna.  
  
 *nID*  
 Číslo ID zdroje pro přiřazení do nově vytvořené ovládacího prvku.  
  
 *pControl*  
 Instanci ovládacího prvku Windows Forms, který má být spojen s [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) objektu (pouze čtvrtý přetížení).  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí nenulovou hodnotu. Pokud je úspěšné, vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří instanci ovládacího prvku rozhraní .NET Framework Windows Forms v MFC kontejner.  
  
 První přetížení metody přijímá datový typ rozhraní .NET Framework *pType* tak, aby MFC můžete vytvořit nový objekt tohoto typu. *pType* musí být [typ](https://msdn.microsoft.com/en-us/library/system.type) datového typu.  
  
 Vytvoří druhý přetížení metody ovládacího prvku Windows Forms na základě `TManagedControl` parametr šablony `CWinFormsControl` třídy. Na základě velikost a umístění ovládacího prvku `RECT` struktura předaný metodě. Pouze *dwStyle* záleží pro stylů.  
  
 Třetí přetížení metody vytvoří ovládacího prvku Windows Forms, který nahrazuje statického ovládacího prvku, zničení ho a za předpokladu, že její umístění, pořadí z-order a stylů. Statické ovládací prvek slouží pouze jako zástupný symbol pro ovládacího prvku Windows Forms. Při vytváření ovládacího prvku, toto přetížení kombinuje styly z *dwStyle* s styly prostředků statické ovládací prvek.  
  
 Čtvrtý přetížení metody umožňuje předat již vytvořenou instanci ovládacího prvku Windows Forms *pControl* , budou zahrnovat MFC. Musí být stejného typu jako `TManagedControl` parametr šablony `CWinFormsControl` třídy.  
  
 V tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) ukázky na pomocí formuláře Windows ovládací prvky.  
  
##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl  
 Vytvoří objekt obálky knihovny MFC Windows Forms ovládací prvek.  
  
```  
CWinFormsControl();
```  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření ovládacího prvku Windows Forms instance při volání [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrol"></a>  CWinFormsControl::GetControl  
 Načte ukazatel ovládacího prvku Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel do ovládacího prvku Windows Forms.  
  
### <a name="example"></a>Příklad  
  V tématu [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle  
 Načte popisovač do ovládacího prvku Windows Forms.  
  
```  
inline HWND GetControlHandle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač do ovládacího prvku Windows Forms.  
  
### <a name="remarks"></a>Poznámky  
 `GetControlHandle` je pomocná metoda, která vrátí popisovač okna, které jsou uložené ve vlastnostech ovládacího prvku rozhraní .NET Framework. Hodnota popisovač okna se zkopíruje do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) během volání [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).  
  
##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;  
 Nahradí [CWinFormsControl::GetControl](#getcontrol) ve výrazech.  
  
```  
inline TManagedControl^  operator->() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor poskytuje pohodlné syntaxe, který nahrazuje `GetControl` ve výrazech.  
  
 Další informace o Windows Forms najdete v tématu [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^  
 Vrhá typu jako ukazatel do ovládacího prvku Windows Forms.  
  
```  
inline operator TManagedControl^() const;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor předá `CWinFormsControl<TManagedControl>` na funkce, které přijímají ukazatel do ovládacího prvku Windows Forms.  
  
## <a name="see-also"></a>Viz také  
 [CWinFormsDialog – třída](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView – třída](../../mfc/reference/cwinformsview-class.md)
