---
title: Makra a funkce pro správu knihoven DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 42a08ff2e806acae6713c9df3fe170f7e89f05af
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751596"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra a funkce pro správu knihoven DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportuje třídy.|
|[Afx_manage_state](#afx_manage_state)|Chraňte exportovnou funkci v dll.|
|[Modul AfxOleInit](#afxoleinitmodule)|Poskytuje podporu OLE z běžné knihovny DLL knihovny MFC, která je dynamicky propojena s knihovnou MFC.|
|[Modul AfxNetInit](#afxnetinitmodule)|Poskytuje podporu soketů knihovny MFC z běžné knihovny DLL knihovny MFC, která je dynamicky propojena se knihovnou MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Získá aktuální stav příznak stavu pro modul.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Nastaví stav modulu před inicializací a/nebo obnovení předchozího stavu modulu po vyčištění.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicializuje dll.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|nastavte příznak stavu pro modul, který ovlivňuje chování rozhraní MFC winsxs.|
|[Afxtermextensionmodule](#afxtermextensionmodule)|Umožňuje knihovně MFC vyčistit knihovnu DLL rozšíření knihovny MFC, když se každý proces odpojí od knihovny DLL.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>Afx_ext_class

[Knihovny DLL rozšíření knihovny MFC](../../build/extension-dlls.md) používají k exportu tříd AFX_EXT_CLASS maker. Spustitelné soubory, které odkazují na knihovnu DLL rozšíření knihovny MFC, používají makro k importu tříd.

### <a name="remarks"></a>Poznámky

S AFX_EXT_CLASS makro, stejné soubory záhlaví používané k vytvoření dll rozšíření knihovny MFC lze použít s spustitelnými soubory, které odkazují na knihovnu DLL.

V souboru záhlaví pro dll přidejte klíčové slovo AFX_EXT_CLASS do deklarace třídy takto:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Další informace naleznete v [tématu Export a import pomocí AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>Afx_manage_state

Volání tohoto makra k ochraně exportované funkce v dll.

### <a name="syntax"></a>Syntaxe

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parametry

*pModulStav*<br/>
Ukazatel na `AFX_MODULE_STATE` strukturu.

### <a name="remarks"></a>Poznámky

Při vyvolání tohoto makra je *pModuleState* efektivní stav modulu pro zbytek okamžité obsahující rozsah. Po opuštění oboru bude automaticky obnoven předchozí stav efektivního modulu.
Struktura `AFX_MODULE_STATE` obsahuje globální data pro modul, to znamená část stavu modulu, který je posunut nebo popped.

Ve výchozím nastavení knihovna MFC používá popisovač prostředků hlavní aplikace k načtení šablony prostředků. Pokud máte exportovnou funkci v knihovně DLL, například tu, která spustí dialogové okno v knihovně DLL, je tato šablona ve skutečnosti uložena v modulu Knihovna DLL. Chcete-li použít správný popisovač, je třeba přepnout stav modulu. Můžete to provést přidáním následujícího kódu na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Tím se zamění aktuální stav modulu se stavem vráceným z [AfxGetStaticModuleState](#afxgetstaticmodulestate) až do konce aktuálního oboru.

Další informace o stavech modulů a knihovně MFC naleznete v části Správa stavových dat modulů knihovny MFC v [tématu Vytváření nových dokumentů, systému Windows a zobrazení](../creating-new-documents-windows-and-views.md) a [technické poznámky 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Když knihovna MFC vytvoří kontext aktivace pro sestavení, používá [AfxWinInit](application-information-and-management.md#afxwininit) k vytvoření kontextu a `AFX_MANAGE_STATE` k jeho aktivaci a deaktivaci. Všimněte `AFX_MANAGE_STATE` si také, že je povoleno pro statické knihovny Knihovny MFC, stejně jako knihovny DLL knihovny MFC, aby byl povolen kód knihovny MFC ke spuštění ve správném kontextu aktivace vybrané knihovny DLL uživatele. Další informace naleznete [v tématu Podpora kontextů aktivace ve stavu modulu knihovny MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>Modul AfxOleInit

Pro podporu OLE z běžné knihovny DLL knihovny MFC, která je dynamicky propojena s knihovnou MFC, volejte tuto funkci v běžné funkci knihovny `CWinApp::InitInstance` MFC DLL a inicializujte knihovnu MFC OLE DLL.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Poznámky

Knihovna MFC OLE DLL je knihovna DLL rozšíření knihovny MFC. V pořadí pro rozšíření knihovny MFC `CDynLinkLibrary` DLL získat kabelové `CDynLinkLibrary` do řetězce, musí vytvořit objekt v kontextu každého modulu, který bude používat. `AfxOleInitModule`vytvoří `CDynLinkLibrary` objekt v kontextu běžné knihovny MFC DLL tak, aby se dostal do řetězce `CDynLinkLibrary` objektů běžné knihovny MFC DLL.

Pokud vytváříte ovládací prvek OLE `COleControlModule`a používáte `AfxOleInitModule` , `InitInstance` neměli `COleControlModule` `AfxOleInitModule`byste volat, protože členská funkce pro volání .

### <a name="requirements"></a>Požadavky

**Záhlaví** \<: afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>Modul AfxNetInit

Pro podporu soketů knihovny MFC z běžné knihovny DLL knihovny MFC, která je dynamicky propojena s knihovnou MFC, přidejte volání této funkce ve `CWinApp::InitInstance` funkci běžné knihovny MFC DLL pro inicializaci knihovny DLL soketů knihovny MFC.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Poznámky

Knihovna DLL soketu knihovny MFC je rozšiřující knihovna DLL knihovny MFC. V pořadí pro rozšíření knihovny MFC `CDynLinkLibrary` DLL získat kabelové `CDynLinkLibrary` do řetězce, musí vytvořit objekt v kontextu každého modulu, který bude používat. `AfxNetInitModule`vytvoří `CDynLinkLibrary` objekt v kontextu běžné knihovny MFC DLL tak, aby se dostal do řetězce `CDynLinkLibrary` objektů běžné knihovny MFC DLL.

### <a name="requirements"></a>Požadavky

**Záhlaví:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Pomocí této funkce můžete získat aktuální stav příznaku stavu modulu, který ovlivňuje chování knihovny MFC systému WinSxS.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota příznaku stavu modulu.

### <a name="remarks"></a>Poznámky

Když je nastaven příznak (což je výchozí) a vlákno zadá modul knihovny MFC (viz [AFX_MANAGE_STATE](#afx_manage_state)), je aktivován kontext modulu.

Pokud příznak není nastaven, kontext modulu není aktivován při vstupu.

Kontext modulu je určen z jeho manifestu, obvykle vložené do prostředků modulu.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

Volání této funkce nastavit stav modulu před inicializace a /nebo obnovit předchozí stav modulu po vyčištění.

### <a name="syntax"></a>Syntaxe

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `AFX_MODULE_STATE` strukturu.

### <a name="remarks"></a>Poznámky

Struktura `AFX_MODULE_STATE` obsahuje globální data pro modul, to znamená část stavu modulu, který je posunut nebo popped.

Ve výchozím nastavení knihovna MFC používá popisovač prostředků hlavní aplikace k načtení šablony prostředků. Pokud máte exportovnou funkci v knihovně DLL, například tu, která spustí dialogové okno v knihovně DLL, je tato šablona ve skutečnosti uložena v modulu Knihovna DLL. Chcete-li použít správný popisovač, je třeba přepnout stav modulu. Můžete to provést přidáním následujícího kódu na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Tím se zamění aktuální stav modulu se stavem vráceným od `AfxGetStaticModuleState` konce aktuálního oboru.

Další informace o stavech modulů a knihovně MFC naleznete v části Správa stavových dat modulů knihovny MFC v [tématu Vytváření nových dokumentů, systému Windows a zobrazení](../creating-new-documents-windows-and-views.md) a [technické poznámky 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Volání této funkce v knihovně DLL rozšíření knihovny `DllMain` MFC pro inicializaci knihovny DLL.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parametry

*Státu*<br/>
Odkaz na [strukturu AFX_EXTENSION_MODULE struktura,](afx-extension-module-structure.md) která bude obsahovat stav modulu DLL rozšíření knihovny MFC po inicializaci. Stav obsahuje kopii objektů třídy runtime, které byly inicializovány knihovnou DLL rozšíření `DllMain` knihovny MFC jako součást normální statické konstrukce objektu provedené před zadáním.

*hModul*<br/>
Popisovač modulu DLL rozšíření knihovny MFC.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je knihovna DLL rozšíření knihovny MFC úspěšně inicializována; jinak NEPRAVDA.

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
...
```

`AfxInitExtensionModule`vytvoří kopii Knihovny HMODULE knihovny DLL a zachytí runtime`CRuntimeClass` třídy DLL (struktury)`COleObjectFactory` a její objektové `CDynLinkLibrary` továrny (objekty) pro pozdější použití při vytvoření objektu.
Knihovny DLL rozšíření knihovny MFC `DllMain` je třeba provést dvě věci v jejich funkci:

- Volejte [AfxInitExtensionModule](#afxinitextensionmodule) a zkontrolujte vrácenou hodnotu.

- Vytvořte `CDynLinkLibrary` objekt, pokud knihovna DLL bude exportovat objekty [CRuntimeClass Structure](cruntimeclass-structure.md) nebo má vlastní prostředky.

Můžete volat `AfxTermExtensionModule` vyčistit knihovnu DLL rozšíření knihovny MFC, když se každý proces odpojí od knihovny DLL rozšíření knihovny MFC `AfxFreeLibrary` (což se stane, když proces ukončí nebo když je knihovna DLL uvolněna v důsledku volání).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Tato funkce slouží k nastavení příznaku stavu modulu, který ovlivňuje chování knihovny MFC systému WinSxS.

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
Nová hodnota příznaku stavu modulu.

### <a name="remarks"></a>Poznámky

Když je nastaven příznak (což je výchozí) a vlákno zadá modul knihovny MFC (viz [AFX_MANAGE_STATE](#afx_manage_state)), je aktivován kontext modulu.
Pokud příznak není nastaven, kontext modulu není aktivován při vstupu.
Kontext modulu je určen z jeho manifestu, obvykle vložené do prostředků modulu.

### <a name="example"></a>Příklad

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>Afxtermextensionmodule

Volání této funkce povolit knihovny MFC vyčistit knihovnu DLL rozšíření knihovny MFC při každém procesu odpojí od Knihovny DLL `AfxFreeLibrary` (což se stane při ukončení procesu nebo při uvolnění knihovny DLL v důsledku volání).

### <a name="syntax"></a>Syntaxe

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parametry

*Státu*<br/>
Odkaz na [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) strukturu, která obsahuje stav modulu DLL rozšíření knihovny MFC.

*Míč*<br/>
Pokud true, vyčistěte všechny moduly DLL rozšíření knihovny MFC. V opačném případě vyčistěte pouze aktuální modul DLL.

### <a name="remarks"></a>Poznámky

`AfxTermExtensionModule`odstraní všechny místní úložiště připojené k modulu a odebere všechny položky z mezipaměti mapy zpráv. Příklad:

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

Pokud aplikace načte a uvolní rozšíření Knihovny DLL knihovny MFC dynamicky, nezapomeňte volat `AfxTermExtensionModule`. Vzhledem k tomu, že většina knihovny DLL rozšíření knihovny MFC nejsou `AfxTermExtensionModule` dynamicky načteny (obvykle jsou propojeny prostřednictvím svých knihoven importu), volání obvykle není nutné.

Knihovny DLL rozšíření knihovny MFC je třeba `DllMain`volat [AfxInitExtensionModule](#afxinitextensionmodule) v jejich . Pokud knihovna DLL bude exportovat objekty [CRuntimeClass](cruntimeclass-structure.md) nebo má vlastní `CDynLinkLibrary` prostředky, musíte také vytvořit objekt v . `DllMain`

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdll_.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
