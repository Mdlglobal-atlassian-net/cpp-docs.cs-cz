---
title: "Makra a funkce pro správu knihoven DLL | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 535045d715651d6393227457068a86f240c27dce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra a funkce pro správu knihoven DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportuje třídy.|
|[AFX_MANAGE_STATE –](#afx_manage_state)|Chraňte exportované funkce v knihovně DLL.|
|[AfxOleInitModule –](#afxoleinitmodule)|Poskytuje podporu OLE z regulární knihovny MFC DLL dynamicky propojené s knihovnou MFC.|
|[Afxnetinitmodule –](#afxnetinitmodule)|Poskytuje podporu MFC Sockets z regulární knihovny MFC DLL dynamicky propojené s knihovnou MFC.|
|[Afxgetambientactctx –](#afxgetambientactctx)|Získá aktuální stav příznak stav modulu.|
|[Afxgetstaticmodulestate –](#afxgetstaticmodulestate)|Nastaví stav modulu před inicializací nebo k obnovení předchozího stavu modulu po vyčištění.|
|[AfxInitExtensionModule]()#afxinitextensionmodule|Inicializuje knihovnu DLL.|
|[Afxsetambientactctx –](#afxsetambientactctx)|nastavte příznak-module stavu, které ovlivňují chování WinSxS MFC.|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|Umožňuje MFC čištění rozšíření MFC DLL při každém odpojení procesu z knihovny DLL.|


## <a name="afx_ext_class"></a>AFX_EXT_CLASS
[MFC – rozšiřující knihovny DLL](../../build/extension-dlls.md) použijte makro **AFX_EXT_CLASS** export tříd, spustitelné soubory, které odkazují MFC – rozšiřující knihovny DLL pomocí makro postup importu tříd.  
   
### <a name="remarks"></a>Poznámky  
 Pomocí **AFX_EXT_CLASS** makro, stejné záhlaví soubory použít k sestavení rozšíření MFC DLL lze použít s spustitelné soubory, které na knihovnu DLL.  
  
 V záhlaví souboru pro knihovny DLL, přidejte **AFX_EXT_CLASS** – klíčové slovo k prohlášení o třídě následujícím způsobem:  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 Další informace najdete v tématu [Export a Import pomocí AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).  
   
### <a name="requirements"></a>Požadavky  
 Záhlaví: **afxv_**dll.h  
   
## <a name="afx_manage_state"></a>AFX_MANAGE_STATE –
Volání této makro k ochraně exportované funkce v knihovně DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>Parametry  
 `pModuleState`  
 Ukazatel na `AFX_MODULE_STATE` struktura.  
   
### <a name="remarks"></a>Poznámky  
 Po vyvolání této makro `pModuleState` je efektivní modul stavu pro zbývající okamžitou obsahující oboru. Při výstupu oboru, předchozí stav efektivní modulu se automaticky obnoví.    
 `AFX_MODULE_STATE` Struktura obsahuje globální data pro modul, který je část stavu modulu, který se instaluje nebo odebrány.    
 Ve výchozím nastavení používá MFC popisovač prostředku hlavní aplikace pro načtení šablony prostředků. Pokud máte exportované funkce v knihovně DLL, například ten, který spouští dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložena v modulu DLL. Budete muset přepnutí stavu modulu pro správné popisovač má být použit. Můžete provést přidáním následující kód do začátku funkce:    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 To umožňuje přepnout aktuální stav modulu se stavem vrácená z [afxgetstaticmodulestate –](#afxgetstaticmodulestate) až do konce aktuálního oboru.    
 Další informace o stavy modulů a knihovna MFC, najdete v části "Správa stavu dat modulů knihovny MFC" v [vytváření nových dokumentů, oken a zobrazení](../creating-new-documents-windows-and-views.md) a [Technická poznámka 58](../tn058-mfc-module-state-implementation.md).    
> [!NOTE]
>  MFC vytvoří aktivační kontext pro sestavení, používá [afxwininit –](#afxwininit) k vytvoření kontextu a `AFX_MANAGE_STATE` aktivovat a deaktivovat. Všimněte si také, že `AFX_MANAGE_STATE` je povolený pro statické knihovny MFC a také MFC – knihovny DLL, aby bylo možné povolit MFC kód na provedení v správný aktivační kontext Vybraná knihovna DLL uživatele. Další informace najdete v tématu [podpora kontextů aktivace ve stavu modulu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).     
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstat_.h  
   
### <a name="see-also"></a>Viz také  
 [Afxgetstaticmodulestate –](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule –
Podpora OLE z regulární knihovny MFC DLL dynamicky propojené s knihovnou MFC volání této funkce ve vašem regulární MFC DLL `CWinApp::InitInstance` funkce inicializace MFC OLE knihovny DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>Poznámky  
 Knihovny MFC OLE DLL je knihovnu DLL; v pořadí pro knihovnu DLL do **CDynLinkLibrary** řetězci, musíte vytvořit **CDynLinkLibrary** objektu v kontextu každý modul, který bude používat ho. `AfxOleInitModule`vytvoří **CDynLinkLibrary** objektu v kontextu vaší regulární MFC DLL tak, aby získá přes drátové sítě do **CDynLinkLibrary** objektu řetězu běžné knihovny MFC DLL.  
  
 Pokud vytváříte ovládacího prvku OLE a používáte `COleControlModule`, by neměl volání **AfxOleInitModule –** protože `InitInstance` – členská funkce pro `COleControlModule` volání `AfxOleInitModule`.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví**: < afxdll_.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxMessageBox –](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>Afxnetinitmodule –
Pro MFC sokety z regulární knihovny MFC DLL dynamicky propojené s knihovnou MFC, přidejte volání této funkce ve vašem regulární MFC DLL **CWinApp::InitInstance** funkce inicializace MFC DLL sokety.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>Poznámky  
 MFC Sockets DLL je knihovnu DLL; v pořadí pro knihovnu DLL do **CDynLinkLibrary** řetězci, musíte vytvořit **CDynLinkLibrary** objektu v kontextu každý modul, který bude používat ho. `AfxNetInitModule`vytvoří **CDynLinkLibrary** objektu v kontextu vaší regulární MFC DLL tak, aby získá přes drátové sítě do **CDynLinkLibrary** objektu řetězu běžné knihovny MFC DLL.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** < afxdll_.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxMessageBox –](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a>Afxgetambientactctx –
Pomocí této funkce můžete získat aktuální stav příznak stavu modulu, který má vliv na chování WinSxS MFC.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>Návratová hodnota  
 Modul stavu příznakem aktuální hodnotu.  
   
### <a name="remarks"></a>Poznámky  
 Když je nastavený příznak (což je výchozí nastavení) a vlákna zadání modul MFC (najdete v části [AFX_MANAGE_STATE](#afx_manage_state)), je aktivována kontextu modulu.  
  
 Pokud není nastavený příznak, kontextu modul není aktivováno, na položku.  
  
 Kontext modulu se určí na základě jeho manifest, obvykle vložený do modulu prostředky.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcomctl32.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE –](#afx_manage_state)   
 [Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md)   
 [Afxsetambientactctx –](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a>Afxgetstaticmodulestate –
Volání této funkce pro nastavení stavu modulu před inicializací nebo po vyčištění obnovit předchozí stav modulu.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `AFX_MODULE_STATE` struktura.  
   
### <a name="remarks"></a>Poznámky  
 `AFX_MODULE_STATE` Struktura obsahuje globální data pro modul, který je část stavu modulu, který se instaluje nebo odebrány.  
  
 Ve výchozím nastavení používá MFC popisovač prostředku hlavní aplikace pro načtení šablony prostředků. Pokud máte exportované funkce v knihovně DLL, například ten, který spouští dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložena v modulu DLL. Budete muset přepnutí stavu modulu pro správné popisovač má být použit. Můžete provést přidáním následující kód do začátku funkce:  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 To umožňuje přepnout aktuální stav modulu se stavem vrácená z `AfxGetStaticModuleState` až do konce aktuálního oboru.  
  
 Další informace o stavy modulů a knihovna MFC, najdete v části "Správa stavu dat modulů knihovny MFC" v [vytváření nových dokumentů, oken a zobrazení](../creating-new-documents-windows-and-views.md) a [Technická poznámka 58](../tn058-mfc-module-state-implementation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule –
Volání této funkce v MFC rozšiřující knihovny DLL na `DllMain` inicializovat knihovnu DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>Parametry  
 `state`  
 Odkaz na [AFX_EXTENSION_MODULE – struktura](afx-extension-module-structure.md) struktura, která bude obsahovat stavu modulu MFC DLL rozšíření po inicializaci. Stav zahrnuje kopii runtime třídy objektů, které byly inicializovány rozšíření MFC DLL jako součást normální statický objekt konstrukce spuštěny před `DllMain` zadána.  
  
 `hModule`  
 Obslužná rutina modulu MFC DLL rozšíření.  
   
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud rozšíření MFC DLL je úspěšně inicializovaný, jinak hodnota **FALSE**.  
   
### <a name="remarks"></a>Poznámky  
 Příklad:  
  
```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

```
  
 `AfxInitExtensionModule`Vytvoří kopii knihovnu DLL **HMODULE** a zachytí knihovnu DLL modulu runtime – třídy (`CRuntimeClass` struktury) i jeho objekt Factory (`COleObjectFactory` objekty) pro použití novější při **CDynLinkLibrary**je vytvořen objekt.    
 MFC – rozšiřující knihovny DLL je potřeba udělat dvě věci v jejich `DllMain` funkce:    
-   Volání [AfxInitExtensionModule](#_mfc_afxinitextensionmodule) a zkontrolujte návratovou hodnotu.   
-   Vytvoření **CDynLinkLibrary** objektu, pokud bude export knihovny DLL [CRuntimeClass struktura](cruntimeclass-structure.md) objekty nebo má svou vlastní vlastní prostředky.    
 Můžete volat `AfxTermExtensionModule` odstranit rozšíření MFC DLL při každém odpojení procesu od rozšíření MFC DLL (který se stane, když proces bude ukončen, nebo když je na základě těchto uvolněna z knihovny DLL `AfxFreeLibrary` volání).     

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdll_.h     

### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule –](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>Afxsetambientactctx –
Pomocí této funkce můžete nastavit příznak stavu modulu, které ovlivňují chování WinSxS MFC.  
   
### <a name="syntax"></a>Syntaxe  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>Parametry  
 `bSet`  
 Nová hodnota příznaku stav modulu.  
   
### <a name="remarks"></a>Poznámky  
 Když je nastavený příznak (což je výchozí nastavení) a vlákna zadání modul MFC (najdete v části [AFX_MANAGE_STATE](#afx_manage_state)), je aktivována kontextu modulu.    
 Pokud není nastavený příznak, kontextu modul není aktivováno, na položku.    
 Kontext modulu se určí na základě jeho manifest, obvykle vložený do modulu prostředky.  
   
### <a name="example"></a>Příklad  
 ```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcomctl32.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [Afxgetambientactctx –](#afxgetambientactctx)   
 [AFX_MANAGE_STATE –](#afx_manage_state)   
 [Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule –

Volání této funkce umožníte MFC čištění rozšíření MFC DLL při každém odpojení procesu z knihovny DLL (který se stane, když proces bude ukončen, nebo když je na základě těchto uvolněna z knihovny DLL `AfxFreeLibrary` volání).  
   
### <a name="syntax"></a>Syntaxe  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>Parametry  
 `state`  
 Odkaz na [AFX_EXTENSION_MODULE –](afx-extension-module-structure.md) struktura, která obsahuje stav rozšíření MFC DLL – modul.  
  
 *Míč*  
 Pokud **TRUE**, vyčistit všechny moduly knihoven DLL rozšíření MFC. Čištění, jinak hodnota aktuální modulu DLL.  
   
### <a name="remarks"></a>Poznámky  
 `AfxTermExtensionModule`Odstraní všechny místní úložiště připojené k modulu a odeberte všechny položky z mezipaměti mapy zpráv. Příklad:  
  
```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}

```
  
 Pokud vaše aplikace načte a uvolní MFC – rozšiřující knihovny DLL dynamicky, nezapomeňte volat `AfxTermExtensionModule`. Protože většina MFC – rozšiřující knihovny DLL dynamicky nenačtou (obvykle, jsou propojeny prostřednictvím jejich knihoven importovat), volání `AfxTermExtensionModule` není obvykle nutné.  
  
 MFC – rozšiřující knihovny DLL muset volat [AfxInitExtensionModule](#afxinitextensionmodule) v jejich `DllMain`. Pokud budete exportovat knihovnu DLL [CRuntimeClass](cruntimeclass-structure.md) objekty nebo má svou vlastní vlastní prostředky, je také nutné vytvořit **CDynLinkLibrary** objekt v `DllMain`.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdll_.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule –](#afxinitextensionmodule)
 




