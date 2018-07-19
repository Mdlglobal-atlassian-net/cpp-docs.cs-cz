---
title: Makra a funkce pro správu knihoven DLL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee79ccad55d2fd360166b9d693f3d4757fe2049f
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339225"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra a funkce pro správu knihoven DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Export tříd.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Ochrana exportované funkce v knihovně DLL.|
|[AfxOleInitModule –](#afxoleinitmodule)|Poskytuje podporu technologie OLE z běžné knihovny MFC DLL staticky propojené do MFC.|
|[Afxnetinitmodule –](#afxnetinitmodule)|Poskytuje podporu soketů knihovny MFC z běžné knihovny MFC DLL staticky propojené do MFC.|
|[Afxgetambientactctx –](#afxgetambientactctx)|Získá aktuální stav příznaku-module stavu.|
|[Afxgetstaticmodulestate –](#afxgetstaticmodulestate)|Nastaví stav modulu před inicializací a/nebo po vyčištění obnovit předchozí stav modulu.|
|[AfxInitExtensionModule]()#afxinitextensionmodule|Inicializuje knihovnu DLL.|
|[Afxsetambientactctx –](#afxsetambientactctx)|nastavte příznak stavu na modul, který má vliv na chování WinSxS knihovny MFC.|
|[AfxTermExtensionModule]()#afxtermextensionmodule)|Umožňuje MFC vyčištění MFC – rozšiřující knihovny DLL při každém odpojení procesu z knihovny DLL.|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS
[MFC – rozšiřující knihovny DLL](../../build/extension-dlls.md) použijte makro AFX_EXT_CLASS Postup exportu tříd, spustitelné soubory, které jsou propojeny do MFC – rozšiřující knihovny DLL použijte makro postup importu tříd.  
   
### <a name="remarks"></a>Poznámky  
 Pomocí AFX_EXT_CLASS – makro jde použít stejné soubory záhlaví sloužící k sestavení MFC – rozšiřující knihovny DLL s spustitelné soubory, které odkazují na knihovny DLL.  
  
 V souboru hlaviček pro vaši knihovnu DLL přidejte klíčové slovo AFX_EXT_CLASS deklaraci vaší třídy následujícím způsobem:  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 Další informace najdete v tématu [Export a Import pomocí AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).  
   
### <a name="requirements"></a>Požadavky  
 Záhlaví: **afxv_** dll.h  
   
## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE
Volání toto makro k ochraně exportované funkce v knihovně DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>Parametry  
 *pModuleState*  
 Ukazatel `AFX_MODULE_STATE` struktury.  
   
### <a name="remarks"></a>Poznámky  
 Při vyvolání toto makra *pModuleState* je efektivní modul stavu pro zbývající okamžité obsahující obor. Při opuštění oboru, budou se automaticky obnoví předchozí stav efektivní modulu.    
 `AFX_MODULE_STATE` Struktura obsahuje globální data modulu, to znamená, část státu modul, který je vloženo nebo odebrán.    
 Ve výchozím nastavení knihovna MFC používá k načtení šablony prostředků popisovač prostředku hlavní aplikace. Pokud máte exportované funkce v knihovně DLL, jako je ten, který spustí dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložené v modul knihovny DLL. Je potřeba přepnout stav modulu pro správné popisovač, který se má použít. To lze provést přidáním následujícího kódu na začátek funkce:    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 To Zamění aktuální stav modulu se stavem vrácená [afxgetstaticmodulestate –](#afxgetstaticmodulestate) až do konce v aktuálním oboru.    
 Další informace o stavy modulů a knihovna MFC naleznete v části "Správa the stav dat modulů knihovny MFC" v [vytváření nových dokumentů, Windows a zobrazení](../creating-new-documents-windows-and-views.md) a [technická Poznámka: 58](../tn058-mfc-module-state-implementation.md).    
> [!NOTE]
>  Knihovna MFC vytvoří aktivační kontext pro sestavení, používá [afxwininit –](#afxwininit) k vytvoření kontextu a `AFX_MANAGE_STATE` aktivovat a deaktivovat. Všimněte si také, že `AFX_MANAGE_STATE` je povolený pro statické knihovny MFC, knihovny DLL MFC, aby bylo možné povolit MFC kód pro spuštění ve správné aktivační kontext zvolila DLL uživatele. Další informace najdete v tématu [podpora kontextů aktivace ve stavu modulu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).     
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstat_.h  
   
### <a name="see-also"></a>Viz také  
 [Afxgetstaticmodulestate –](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule –
Pro podporu technologie OLE z běžné knihovny MFC DLL staticky propojené do MFC, volejte tuto funkce ve vaší běžné knihovny MFC DLL `CWinApp::InitInstance` funkce lze inicializovat OLE Knihovnu MFC.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>Poznámky  
 MFC OLE knihovny DLL je rozšiřující knihovny DLL; MFC aby rozšiřující knihovny DLL MFC do `CDynLinkLibrary` řetěz, musíte vytvořit `CDynLinkLibrary` objektu v kontextu každého modulu, který budete používat ho. `AfxOleInitModule` vytvoří `CDynLinkLibrary` objektu v kontextu vašeho běžné knihovny MFC DLL tak, aby získá zapojenými do `CDynLinkLibrary` objektu řetězce běžné knihovny MFC DLL.  
  
 Pokud vytváříte ovládacího prvku OLE a používáte `COleControlModule`, neměli by jste volat `AfxOleInitModule` protože `InitInstance` členskou funkci pro `COleControlModule` volání `AfxOleInitModule`.  
   
### <a name="requirements"></a>Požadavky  
 **Hlavička**: < afxdll_.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  Afxnetinitmodule –
Pro podporu soketů knihovny MFC z běžné knihovny MFC DLL staticky propojené do MFC, přidejte volání pro tuto funkci ve vaší běžné knihovny MFC DLL `CWinApp::InitInstance` funkce za účelem inicializace soketů knihovny MFC DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>Poznámky  
 Rozšiřující knihovny DLL; MFC je soketů knihovny MFC DLL aby rozšiřující knihovny DLL MFC do `CDynLinkLibrary` řetěz, musíte vytvořit `CDynLinkLibrary` objektu v kontextu každého modulu, který budete používat ho. `AfxNetInitModule` vytvoří `CDynLinkLibrary` objektu v kontextu vašeho běžné knihovny MFC DLL tak, aby získá zapojenými do `CDynLinkLibrary` objektu řetězce běžné knihovny MFC DLL.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** < afxdll_.h >  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> Afxgetambientactctx –
Tuto funkci použijte, chcete-li získat aktuální stav, stav příznaku-module, který má vliv na chování WinSxS knihovny MFC.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>Návratová hodnota  
 Modul stavu aktuální hodnota příznaku.  
   
### <a name="remarks"></a>Poznámky  
 Když je příznak nastaven (což je výchozí hodnota) a vlákno zadá modul knihovny MFC (naleznete v tématu [AFX_MANAGE_STATE](#afx_manage_state)), je aktivováno kontext modulu.  
  
 Pokud není nastavený příznak, není v položka aktivována kontext modulu.  
  
 Kontext modulu je určen z manifestu, obvykle vložený do prostředků modulu.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcomctl32.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md)   
 [Afxsetambientactctx –](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a> Afxgetstaticmodulestate –
Voláním této funkce nastavit stav modulu před inicializací a/nebo po vyčištění obnovit předchozí stav modulu.  
   
### <a name="syntax"></a>Syntaxe    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `AFX_MODULE_STATE` struktury.  
   
### <a name="remarks"></a>Poznámky  
 `AFX_MODULE_STATE` Struktura obsahuje globální data modulu, to znamená, část státu modul, který je vloženo nebo odebrán.  
  
 Ve výchozím nastavení knihovna MFC používá k načtení šablony prostředků popisovač prostředku hlavní aplikace. Pokud máte exportované funkce v knihovně DLL, jako je ten, který spustí dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložené v modul knihovny DLL. Je potřeba přepnout stav modulu pro správné popisovač, který se má použít. To lze provést přidáním následujícího kódu na začátek funkce:  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 To Zamění aktuální stav modulu se stavem vrácená `AfxGetStaticModuleState` až do konce v aktuálním oboru.  
  
 Další informace o stavy modulů a knihovna MFC naleznete v části "Správa the stav dat modulů knihovny MFC" v [vytváření nových dokumentů, Windows a zobrazení](../creating-new-documents-windows-and-views.md) a [technická Poznámka: 58](../tn058-mfc-module-state-implementation.md).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a> AfxInitExtensionModule
Volejte tuto funkce ve rozšiřující knihovny DLL MFC na `DllMain` inicializace knihovny DLL.  
   
### <a name="syntax"></a>Syntaxe    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>Parametry  
 *Stav*  
 Odkaz na [AFX_EXTENSION_MODULE – struktura](afx-extension-module-structure.md) struktura, která bude obsahovat stavu modul knihovny DLL MFC rozšíření po inicializaci. Stav zahrnuje kopírování objektů tříd modulu runtime, které byly inicializovány pomocí MFC – rozšiřující knihovny DLL jako součást normální statický objekt konstrukce spuštěny před `DllMain` zadání.  
  
 *hModule*  
 Popisovač rozšiřující modul knihovny DLL MFC.  
   
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšně inicializovaný MFC – rozšiřující knihovny DLL. v opačném případě hodnota FALSE.  
   
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
  
 `AfxInitExtensionModule` Vytvoří kopii HMODULE knihovny DLL a zachytává knihovnu DLL modulu runtime – třídy (`CRuntimeClass` struktury) i jeho objekty pro vytváření objektů (`COleObjectFactory` objektů) pro použití novější při `CDynLinkLibrary` je vytvořen objekt.    
 MFC – rozšiřující knihovny DLL je potřeba udělat dvě věci v jejich `DllMain` funkce:    
-   Volání [AfxInitExtensionModule](#_mfc_afxinitextensionmodule) a ověřte návratovou hodnotu.   
-   Vytvoření `CDynLinkLibrary` objektu, pokud se Export knihovny DLL [CRuntimeClass – struktura](cruntimeclass-structure.md) objekty nebo má svůj vlastní vlastní prostředky.    
 Můžete volat `AfxTermExtensionModule` vyčistit MFC – rozšiřující knihovny DLL při každém odpojení procesu z MFC – rozšiřující knihovny DLL (který se stane při ukončení procesu, nebo pokud kvůli uvolnění knihovny DLL `AfxFreeLibrary` volání).     

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdll_.h     

### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxTermExtensionModule](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>  Afxsetambientactctx –
Pomocí této funkce můžete nastavit příznak stavu na modul, který má vliv na chování WinSxS knihovny MFC.  
   
### <a name="syntax"></a>Syntaxe  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>Parametry  
 *bSet*  
 Nová hodnota příznaku stav modulu.  
   
### <a name="remarks"></a>Poznámky  
 Když je příznak nastaven (což je výchozí hodnota) a vlákno zadá modul knihovny MFC (naleznete v tématu [AFX_MANAGE_STATE](#afx_manage_state)), je aktivováno kontext modulu.    
 Pokud není nastavený příznak, není v položka aktivována kontext modulu.    
 Kontext modulu je určen z manifestu, obvykle vložený do prostředků modulu.  
   
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
 [AFX_MANAGE_STATE](#afx_manage_state)   
 [Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>  AfxTermExtensionModule

Voláním této funkce umožňující knihovny MFC k vyčištění MFC – rozšiřující knihovny DLL při každém odpojení procesu z knihovny DLL (který se stane při ukončení procesu, nebo pokud kvůli uvolnění knihovny DLL `AfxFreeLibrary` volání).  
   
### <a name="syntax"></a>Syntaxe  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>Parametry  
 *Stav*  
 Odkaz na [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) struktura, která obsahuje informace o stavu modulu MFC DLL rozšíření.  
  
 *Koule*  
 Pokud TRUE, vyčistit všechny moduly knihoven DLL rozšíření MFC. Jinak, čištění aktuální modul knihovny DLL.  
   
### <a name="remarks"></a>Poznámky  
 `AfxTermExtensionModule` Odstraní všechny místní úložiště připojené k modulu a odebrat všechny položky z mezipaměti mapování zprávy. Příklad:  
  
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
  
 Pokud vaše aplikace načte nebo uvolní MFC – rozšiřující knihovny DLL dynamicky, je nutné volat `AfxTermExtensionModule`. Protože většina MFC – rozšiřující knihovny DLL nejsou načtené dynamicky (obvykle jsou propojeny prostřednictvím jejich knihovny importu), volání `AfxTermExtensionModule` není obvykle nutné.  
  
 MFC – rozšiřující knihovny DLL musí volat [AfxInitExtensionModule](#afxinitextensionmodule) v jejich `DllMain`. Pokud budete exportovat knihovnu DLL [CRuntimeClass](cruntimeclass-structure.md) objekty nebo má svůj vlastní vlastní prostředky, je také potřeba vytvořit `CDynLinkLibrary` objektu v `DllMain`.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdll_.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [AfxInitExtensionModule](#afxinitextensionmodule)
 




