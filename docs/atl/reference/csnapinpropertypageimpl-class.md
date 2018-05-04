---
title: Třída CSnapInPropertyPageImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 13714553bdf926b00bd4dd76e039d89c7f78f959
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl – třída
Tato třída poskytuje metody pro implementaci objekt modul snap-in Vlastnosti stránky.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
CSnapInPropertyPageImpl : public CDialogImplBase
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Stav změní **OK** a **zrušit** tlačítka.|  
|[CSnapInPropertyPageImpl::Create](#create)|Inicializuje nově vytvořený `CSnapInPropertyPageImpl` objektu.|  
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Voláno rámcem, když uživatel klikne **použít nyní** tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Voláno rámcem, když uživatel klikne **pomoci** tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Voláno rámcem, pokud aktuální stránku už není aktivní.|  
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Voláno rámcem, když uživatel klikne **zrušit** tlačítko a před neproběhla Storno.|  
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Voláno rámcem, když uživatel klikne **resetovat** tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Voláno rámcem, když se stane aktivní aktuální stránku.|  
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Voláno rámcem, když uživatel klikne **zpět** tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Voláno rámcem, když uživatel klikne **Dokončit** tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Voláno rámcem, když uživatel klikne `Next` tlačítko při použití Průvodce typu vlastností.|  
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Předává aktuální zprávu na všechny stránky vlastností.|  
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Volání aktivovat nebo deaktivovat **použít nyní** tlačítko.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Windows **PROPSHEETPAGE** struktura používané `CSnapInPropertyPageImpl` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CSnapInPropertyPageImpl` poskytuje základní implementaci pro objekt, který modul snap-in vlastnost stránky. Základní funkce stránky vlastností modulu snap-in jsou implementovány pomocí několika různých rozhraní a mapování typů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDialogImplBase`  
  
 `CSnapInPropertyPageImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsnap.h  
  
##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose  
 Po neopravitelné změn dat na stránce vlastností modální volání této funkce.  
  
```
void CancelToClose();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce se změní **OK** tlačítko pro **Zavřít** a zakázat **zrušit** tlačítko. Tato změna výstrahy, které uživatele, že je změna trvalé a změny nelze zrušit.  
  
 `CancelToClose` – Členská funkce se nic nestane. v nemodálního seznamu vlastností, protože nemá nemodálního seznamu vlastností **zrušit** tlačítko ve výchozím nastavení.  
  
##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl  
 Vytvoří `CSnapInPropertyPageImpl` objektu.  
  
```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTitle`  
 [v] Název stránky vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li inicializovat podkladová struktura, volejte [CSnapInPropertyPageImpl::Create](#create).  
  
##  <a name="create"></a>  CSnapInPropertyPageImpl::Create  
 Volání této funkce k chybě při inicializaci podkladová struktura stránku vlastností.  
  
```
HPROPSHEETPAGE Create();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro **PROPSHEETPAGE** struktura obsahující atributy nově vytvořený vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Měli byste nejprve zavolat [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) před voláním této funkce.  
  
##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp  
 `m_psp` je struktura, jejíž členové uložení charakteristika **PROPSHEETPAGE**.  
  
```
PROPSHEETPAGE m_psp;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato struktura použijte k chybě při inicializaci vzhled stránky vlastností po je vytvořený.  
  
 Další informace o tuto strukturu, včetně seznamu svých členů, najdete v části [PROPSHEETPAGE](http://msdn.microsoft.com/library/aa815151) ve Windows SDK.  
  
##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply  
 Tato funkce člen je volána, když uživatel klikne **OK** nebo **použít nyní** tlačítko.  
  
```
BOOL OnApply();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jsou přijata změny; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Před `OnApply` lze volat ve rozhraní, můžete musí mít název `SetModified` a nastavit jeho parametr na **TRUE**. Tím se aktivují **použít nyní** tlačítko Jakmile uživatel provede změny na stránce vlastností.  
  
 Přepsání této funkci člen můžete určit, jakou akci váš program provede, když uživatel klikne **použít nyní** tlačítko. Při přepsání, by měla vrátit funkce **TRUE** kvůli přijetí změn a **FALSE** zabránit změny neprojeví.  
  
 Výchozí implementaci `OnApply` vrátí **TRUE**.  
  
##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp  
 Tato funkce člen je volána, když uživatel klikne **pomoci** tlačítko pro stránku vlastností.  
  
```
void OnHelp();
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit nápovědu pro stránku vlastností funkci člena přepište.  
  
##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive  
 Tento člen funkce je volána, když stránky již není aktivní stránku.  
  
```
BOOL OnKillActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud dat bylo úspěšně aktualizováno; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci k provádění úloh ověření speciální data přepište.  
  
##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel  
 Tato funkce člen je volána, když uživatel klikne **zrušit** tlačítko a před zrušit akci neproběhla.  
  
```
BOOL OnQueryCancel();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Povolit operace zrušení; nenulové hodnoty jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přepsat tuto členskou funkci k určení akce program provede, když uživatel klikne **zrušit** tlačítko.  
  
 Výchozí implementaci `OnQueryCancel` vrátí **TRUE**.  
  
##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset  
 Tato funkce člen je volána, když uživatel klikne **zrušit** tlačítko.  
  
```
void OnReset();
```  
  
### <a name="remarks"></a>Poznámky  
 Když tato funkce je volána, se změní na všechny stránky vlastností, které byly provedeny uživatelem dříve kliknutím na **použít nyní** tlačítko jsou zahozeny a seznamu vlastností zachová fokus.  
  
 Přepsání této funkci člen můžete určit, jakou akci provede program, když uživatel klikne **zrušit** tlačítko.  
  
##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive  
 Tento člen funkce je volána, když na stránce je volená uživatelem a stránkou bude aktivní.  
  
```
BOOL OnSetActive();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně nastaven active; stránky jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci k provádění úloh, když je aktivován stránky přepište. Přepsání této členské funkce by měly volat výchozí verze, než se provádí další zpracování.  
  
 Výchozí implementace vrací **TRUE**.  
  
##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack  
 Tato funkce člen je volána, když uživatel klikne **zpět** tlačítka na průvodce.  
  
```
BOOL OnWizardBack();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
-   0 pro automatický přechod na předchozí stránku.  
  
-   -1 zabránit ve změně stránky.  
  
 Přejít na stránku než další, vrátí identifikátor dialogových oken, který se má zobrazit.  
  
### <a name="remarks"></a>Poznámky  
 Funkci člena na některé akce, uživatel musí přijmout při přepsat **zpět** po kliknutí na tlačítko.  
  
##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish  
 Tato funkce člen je volána, když uživatel klikne **Dokončit** tlačítka na průvodce.  
  
```
BOOL OnWizardFinish();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud seznamu vlastností je zrušen po dokončení Průvodce; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Funkci člena na některé akce, uživatel musí přijmout při přepsat **Dokončit** po kliknutí na tlačítko.  
  
##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext  
 Tato funkce člen je volána, když uživatel klikne `Next` tlačítka na průvodce.  
  
```
BOOL OnWizardNext();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
-   0 pro automatický přechod na další stránku.  
  
-   -1 zabránit ve změně stránky.  
  
 Přejít na stránku než další, vrátí identifikátor dialogových oken, který se má zobrazit.  
  
### <a name="remarks"></a>Poznámky  
 Funkci člena na některé akce, uživatel musí přijmout při přepsat `Next` po kliknutí na tlačítko.  
  
##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings  
 Volání této funkce člen přeposílat zprávy na každou stránku v seznamu vlastností.  
  
```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `wParam`  
 [v] Určuje další informace závislé na zprávy.  
  
 `lParam`  
 [v] Určuje další informace závislé na zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud zpráva by neměl předají na další stránku vlastností. jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Pokud na stránce vrátí nenulovou hodnotu, seznam vlastností není odeslat zprávu pro následné stránky.  
  
##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified  
 Volání této funkce člen, pokud chcete povolit nebo zakázat **použít nyní** tlačítko založené na tom, jestli bude použito nastavení na stránce vlastností příslušný externí objekt.  
  
```
void SetModified(BOOL bChanged = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bChanged`  
 [v] **TRUE** k označení, že od poslední se uplatňují; byl změněn nastavení stránky vlastností **FALSE** že aplikovala nastavení vlastností stránky, nebo třeba ji ignorovat.  
  
### <a name="remarks"></a>Poznámky  
 Seznam vlastností udržuje sledování, které jsou stránky "nečisté", který je, stránky vlastností, pro které se mají volat **SetModified (TRUE)**. **Použít nyní** tlačítko bude vždy povolená při volání **SetModified (TRUE)** pro jednu ze stránek. **Použít nyní** tlačítko bude zakázáno, při volání **SetModified (FALSE)** pro jednu ze stránek, ale jen pokud žádný z dalších stránek je "nekonzistentní."  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
