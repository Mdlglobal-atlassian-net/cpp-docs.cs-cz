---
title: Třída CDataPathProperty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2559b4917f16bb8ddc49b73ace8bda6e1a9bafc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty – třída
Implementuje OLE řídit vlastnost, která mohou být načteny asynchronně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Vytvoří `CDataPathProperty` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Načte asynchronní OLE ovládací prvek související s `CDataPathProperty` objektu.|  
|[CDataPathProperty::GetPath](#getpath)|Načte vlastnosti názvu cesty.|  
|[CDataPathProperty::Open](#open)|Zahájí načítání asynchronní vlastnosti přidružené ovládacího prvku ActiveX (OLE).|  
|[CDataPathProperty::ResetData](#resetdata)|Volání `CAsyncMonikerFile::OnDataAvailable` oznámit kontejneru, které se změnily vlastnosti ovládacích prvků.|  
|[CDataPathProperty::SetControl](#setcontrol)|Nastaví asynchronní ovládací prvek ActiveX (OLE) související s vlastností.|  
|[CDataPathProperty::SetPath](#setpath)|Nastaví vlastnosti názvu cesty.|  
  
## <a name="remarks"></a>Poznámky  
 Po spuštění synchronní jsou načteny asynchronní vlastnosti.  
  
 Třída `CDataPathProperty` je odvozený od **CAysncMonikerFile**. Implementovat asynchronní vlastnosti v ovládacích prvků OLE, odvození třídy z `CDataPathProperty`a přepsat [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Další informace o tom, jak použít asynchronní monikery a ovládací prvky ActiveX v internetových aplikací najdete v následujících článcích:  
  
- [Internet první kroky: Ovládací prvky ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internetu první kroky: Asynchronní Monikery](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 Vytvoří `CDataPathProperty` objektu.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Ukazatel na objekt ovládacího prvku OLE mají být spojeny s tímto `CDataPathProperty` objektu.  
  
 `lpszPath`  
 Cesta, která může být absolutní nebo relativní, použít k vytvoření asynchronní přezdívka, který odkazuje na skutečnou absolutní umístění vlastnosti. `CDataPathProperty` adresy URL, ne názvy souborů používá. Pokud chcete `CDataPathProperty` objektu pro soubor, předřadit `file://` k cestě.  
  
### <a name="remarks"></a>Poznámky  
 `COleControl` Objektu na kterou odkazuje `pControl` používá **otevřete** a načíst odvozené třídy. Pokud `pControl` je **NULL**, ovládací prvek použít s **otevřete** musí být nastavená s `SetControl`. Pokud `lpszPath` je **NULL**, můžete předat v cestě prostřednictvím **otevřete** nebo nastavte její `SetPath`.  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 Volání této funkce člen načíst `COleControl` objekt přidružený k `CDataPathProperty` objektu.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí přidružený ukazatel do ovládacího prvku OLE `CDataPathProperty` objektu. **NULL** Pokud není ovládací prvek je spojen.  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 Volání této funkce člen chcete načíst cestu, nastavte, kdy `CDataPathProperty` objekt byl vytvořený, nebo zadaný v **otevřete**, nebo je zadána v předchozích volání `SetPath` – členská funkce.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí název cesty přímo pro vlastnost. Může být prázdný, pokud nebyla zadána žádná cesta.  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 Volání této funkce člen zahájíte načítání asynchronní vlastnosti pro související ovládací prvek.  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Ukazatel na objekt ovládacího prvku OLE mají být spojeny s tímto `CDataPathProperty` objektu.  
  
 `pError`  
 Ukazatel na výjimky souborů. V případě chyby bude nastavena pro příčinu.  
  
 `lpszPath`  
 Cesta, která může být absolutní nebo relativní, použít k vytvoření asynchronní přezdívka, který odkazuje na skutečnou absolutní umístění vlastnosti. `CDataPathProperty` adresy URL, ne názvy souborů používá. Pokud chcete `CDataPathProperty` objektu pro soubor, předřadit `file://` k cestě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce se pokusí získat `IBindHost` rozhraní z ovládacího prvku.  
  
 Před voláním **otevřete** bez cesty, musí být nastavena hodnota vlastnosti cesty. To lze provést, pokud je objekt vytvořený, nebo při volání `SetPath` – členská funkce.  
  
 Před voláním **otevřete** bez řízení, může být přidružený k objektu ovládacího prvku ActiveX (dříve označované jako ovládací prvek OLE). To lze provést, pokud je objekt vytvořený, nebo voláním `SetControl`.  
  
 Všechny přetížení [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) jsou dostupné i z `CDataPathProperty`.  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 Volání této funkce můžete získat `CAsyncMonikerFile::OnDataAvailable` kontejneru upozornit, že vlastnosti ovládacích prvků změnily, a všechny informace načíst asynchronně již není používána.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Poznámky  
 Otevírání by měla být restartována. Odvozené třídy mohou přepsat tuto funkci pro různé výchozí hodnoty.  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 Volání této funkce člen přidružit prvek asynchronní OLE s `CDataPathProperty` objektu.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Ukazatel na asynchronní ovládací prvek OLE být přidružená vlastnost.  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 Volání této funkce člen k nastavení názvu cesty vlastnosti.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPath`  
 Cesta, která může být absolutní nebo relativní pro vlastnost načítá asynchronně. `CDataPathProperty` adresy URL, ne názvy souborů používá. Pokud chcete `CDataPathProperty` objektu pro soubor, předřadit `file://` k cestě.  
  
## <a name="see-also"></a>Viz také  
 [Obrázek ukázkové MFC](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile – třída](../../mfc/reference/casyncmonikerfile-class.md)
