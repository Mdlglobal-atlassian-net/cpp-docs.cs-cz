---
title: Třída COlePropertiesDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d61d773e2c35bb67f34ae2b4a989a388d8b4015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog – třída
Zapouzdří dialogové okno Vlastnosti objektu OLE systému Windows běžné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Vytvoří `COlePropertiesDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživateli proveďte výběr.|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Voláno rámcem při škálování položka document došlo ke změně.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|Struktura sloužící k chybě při inicializaci stránce "Obecné" `COlePropertiesDialog` objektu.|  
|[COlePropertiesDialog::m_lp](#m_lp)|Struktura sloužící k chybě při inicializaci na stránce "Link" `COlePropertiesDialog` objektu.|  
|[COlePropertiesDialog::m_op](#m_op)|Struktura sloužící k chybě při inicializaci `COlePropertiesDialog` objektu.|  
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura použít k přidání další vlastní stránky vlastností.|  
|[COlePropertiesDialog::m_vp](#m_vp)|Struktura sloužící k přizpůsobení stránce "Zobrazit" `COlePropertiesDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Společná dialogová okna vlastnosti objektu OLE poskytují snadný způsob, jak zobrazit a upravit vlastnosti položky OLE dokumentu v souladu s normami systému Windows. Tyto vlastnosti zahrnují mimo jiné informace o souboru reprezentována položku dokumentu, možnosti zobrazení ikonu a škálování bitové kopie a informace na odkaz položky (Pokud je položka připojena).  
  
 Použít `COlePropertiesDialog` objektu, nejprve vytvořit objekt pomocí `COlePropertiesDialog` konstruktor. Po dialogové okno byla vytvořená, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživatelům změnit jakékoli vlastnosti položky. `DoModal` Vrátí, zda uživatel vybral OK ( **IDOK**) nebo Storno ( **IDCANCEL**) tlačítko. Kromě tlačítka OK a zrušit je tlačítko použít. Když uživatel vybere použít, všechny změny vlastností dokumentu položky se použijí na položku a jeho image se automaticky aktualizuje, ale zůstává aktivní.  
  
 [M_psh](#m_psh) – datový člen je ukazatel na **PROPSHEETHEADER** struktura a ve většině případů nebude nutné explicitně k němu přístup. Jedinou výjimkou je, pokud budete potřebovat další stránky vlastností nad rámec stránky Obecné, zobrazení a odkaz výchozí. V takovém případě můžete upravit `m_psh` – datový člen zahrnout svoje vlastní stránky před voláním `DoModal` – členská funkce.  
  
 Další informace o dialogových oknech OLE, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog  
 Vytvoří `COlePropertiesDialog` objektu.  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel na položku dokumentu, jehož vlastnosti jsou spuštěny.  
  
 *nScaleMin*  
 Minimální velikost v procentech pro obrázek položky dokumentu.  
  
 *nScaleMax*  
 Maximální velikost v procentech pro obrázek položky dokumentu.  
  
 `pParentWnd`  
 Ukazatel na nadřazené nebo vlastníka dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Odvození vlastní běžné třídy dialogového okna vlastnosti objektu OLE z `COlePropertiesDialog` kvůli implementaci škálování pro vaši položky dokumentů. Všechna dialogová okna implementované instance této třídy nebude podporovat škálování položky dokumentu.  
  
 Ve výchozím nastavení běžné dialogové okno Vlastnosti objektu OLE má tři výchozí stránky:  
  
-   Obecné  
  
     Tato stránka obsahuje informace o systému pro soubor reprezentována položce vybraný dokument. Uživatel z této stránky můžete převést vybrané položky jiného typu.  
  
-   Zobrazit  
  
     Tato stránka obsahuje možnosti pro zobrazení položky, změna ikonu a změna měřítka obrázku.  
  
-   Odkaz  
  
     Tato stránka obsahuje možnosti pro změnu umístění propojené položky a aktualizaci propojené položky. Z této stránky můžete rozdělit uživatele odkaz vybrané položky.  
  
 Chcete-li přidat stránky nad rámec těch, ve výchozím nastavení provádí, změňte [m_psh](#m_psh) členské proměnné před ukončením konstruktoru vaší `COlePropertiesDialog`-odvozené třídy. Toto je pokročilé implementace `COlePropertiesDialog` konstruktor.  
  
##  <a name="domodal"></a>  COlePropertiesDialog::DoModal  
 Volání této funkce člen povolit uživatelům zobrazit nebo změnit různé vlastnosti položky dokument a zobrazit dialogové okno Vlastnosti objektu OLE Windows běžné.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL** Pokud úspěšná, jinak hodnota 0. **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
 Pokud **IDCANCEL** se vrátí, můžete volat Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp  
 Struktura typu [OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)používané k chybě při inicializaci stránku Obecné dialogového okna vlastnosti objektu OLE.  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato stránka zobrazuje typ a velikost vložení a umožňuje uživatelům přístup k dialogové okno Převést. Tato stránka zobrazuje také cílový odkaz, zda je objekt odkaz.  
  
 Další informace o **OLEUIGNRLPROPS** struktury, najdete v části Windows SDK.  
  
##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp  
 Struktura typu [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)používané k inicializaci stránky odkaz dialogového okna vlastnosti objektu OLE.  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato stránka zobrazuje umístění propojené položky a umožňuje uživatelům aktualizovat nebo zrušit propojení s položky.  
  
 Další informace o **OLEUILINKPROPS** struktury, najdete v části Windows SDK.  
  
##  <a name="m_op"></a>  COlePropertiesDialog::m_op  
 Struktura typu [OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199)používané k chybě při inicializaci běžné dialogové okno Vlastnosti objektu OLE.  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato struktura obsahuje členy použitý k inicializaci stránky Obecné, odkaz a zobrazení.  
  
 Další informace najdete v tématu **OLEUIOBJECTPROPS** a [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) struktury v sadě Windows SDK.  
  
##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh  
 Struktura typu [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546), jejíž členové uložení charakteristiky objektu dialogového okna.  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `COlePropertiesDialog` objekt, můžete použít `m_psh` nastavit různé aspekty dialogu před voláním `DoModal` – členská funkce.  
  
 Pokud změníte `m_psh` – datový člen přímo, přepíše jakékoli výchozí chování.  
  
 Další informace o **PROPSHEETHEADER** struktury, najdete v části Windows SDK.  
  
##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp  
 Struktura typu [OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)používané k inicializaci stránky zobrazení dialogového okna vlastnosti objektu OLE.  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato stránka umožňuje uživatelům přepínat mezi "obsah" a "ikony" zobrazení objektu a změňte jeho škálování v kontejneru. Také umožňuje uživatelům přístup k dialogu ikonu změnit, když objekt se zobrazuje jako ikona.  
  
 Další informace o **OLEUIVIEWPROPS** struktury, najdete v části Windows SDK.  
  
##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale  
 Voláno rámcem, pokud došlo ke změně hodnoty měřítka a OK nebo použít byl vybrán.  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel na položku dokumentu, jehož vlastnosti jsou spuštěny.  
  
 `nCurrentScale`  
 Číselná hodnota měřítka, dialogové okno.  
  
 *bRelativeToOrig*  
 Určuje, zda škálování platí pro původní velikost položky dokumentu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou zpracovávány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Je nutné přepsat tuto funkci povolit škálování ovládací prvky.  
  
> [!NOTE]
>  Před zobrazením běžné dialogové okno Vlastnosti objektu OLE, tato funkce se volá framework **NULL** pro `pItem` a -1 pro `nCurrentScale`. To slouží k určení, zda by měl být povolený škálování ovládací prvky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC str](../../visual-cpp-samples.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [CPropertyPage – třída](../../mfc/reference/cpropertypage-class.md)
