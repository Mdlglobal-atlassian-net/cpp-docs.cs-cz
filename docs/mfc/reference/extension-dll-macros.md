---
title: Makra a funkce pro správu knihoven DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: b27f8763b60dc7ce3ee074cad1365e7e1de3a7e6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854543"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra a funkce pro správu knihoven DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Exportuje třídy.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Chraňte exportovanou funkci v knihovně DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Poskytuje podporu technologie OLE z běžné knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Poskytuje podporu soketů MFC z běžné knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Načte aktuální stav příznaku stavu pro jednotlivé moduly.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Nastaví stav modulu před inicializací nebo obnovení předchozího stavu modulu po vyčištění.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicializuje knihovnu DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Nastavte příznak stavu pro jednotlivé moduly, který má vliv na WinSxS chování knihovny MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Umožňuje knihovně MFC vyčistit knihovnu DLL rozšíření MFC, když se každý proces odpojí od knihovny DLL.|

## <a name="afx_ext_class"></a>AFX_EXT_CLASS

[Knihovny DLL rozšíření MFC](../../build/extension-dlls.md) používají AFX_EXT_CLASS makra k exportu tříd; spustitelné soubory, které odkazují na rozšiřující DLL knihovny MFC, používají makro pro Import tříd.

### <a name="remarks"></a>Poznámky

Pomocí makra AFX_EXT_CLASS lze použít stejné hlavičkové soubory použité k sestavení knihovny MFC rozšíření DLL pro spustitelné soubory, které odkazují na knihovnu DLL.

V hlavičkovém souboru pro knihovnu DLL přidejte klíčové slovo AFX_EXT_CLASS k deklaraci vaší třídy následujícím způsobem:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Další informace najdete v tématu [Export a import pomocí AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXV_DLL. h

## <a name="afx_manage_state"></a>AFX_MANAGE_STATE

Zavolejte toto makro k ochraně exportované funkce v knihovně DLL.

### <a name="syntax"></a>Syntaxe

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parametry

*pModuleState*<br/>
Ukazatel na strukturu `AFX_MODULE_STATE`.

### <a name="remarks"></a>Poznámky

Při vyvolání tohoto makra je *pModuleState* platným stavem modulu pro zbytek bezprostředního nadřazeného oboru. Po ukončení tohoto oboru se automaticky obnoví předchozí efektivní stav modulu.
Struktura `AFX_MODULE_STATE` obsahuje globální data pro modul, to znamená část stavu modulu, která je vložena nebo vyjmuta.

Ve výchozím nastavení používá knihovna MFC popisovač prostředků hlavní aplikace pro načtení šablony prostředku. Pokud máte exportovanou funkci v knihovně DLL, jako je například jedna, která spustí dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložena v modulu knihovny DLL. Aby bylo možné použít správný popisovač, je nutné přepnout stav modulu. To lze provést přidáním následujícího kódu na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Tím se zahodí aktuální stav modulu se stavem vráceným z [AfxGetStaticModuleState](#afxgetstaticmodulestate) do konce aktuálního oboru.

Další informace o stavech modulů a knihovně MFC naleznete v tématu "Správa údajů o stavu modulů knihovny MFC" v tématu [vytváření nových dokumentů, oken a zobrazení](../creating-new-documents-windows-and-views.md) a [technické poznámky 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
>  Když knihovna MFC vytvoří aktivační kontext pro sestavení, používá [AfxWinInit](application-information-and-management.md#afxwininit) k vytvoření kontextu a `AFX_MANAGE_STATE` k jeho aktivaci a deaktivaci. Všimněte si také, že `AFX_MANAGE_STATE` je povolena pro statické knihovny MFC a také knihovny MFC DLL, aby bylo možné spustit kód knihovny MFC ve správném aktivačním kontextu vybraném pomocí knihovny DLL uživatele. Další informace najdete v tématu [Podpora kontextů aktivace ve stavu modulu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxstat_. h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

Pro podporu technologie OLE z běžné knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC, zavolejte tuto funkci ve vaší regulární funkci knihovny MFC DLL `CWinApp::InitInstance` k inicializaci knihovny MFC OLE DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Poznámky

Knihovna MFC OLE DLL je rozšiřující knihovna MFC DLL; aby knihovna DLL rozšíření knihovny MFC mohla být zapojená do `CDynLinkLibrary`ho řetězce, musí vytvořit objekt `CDynLinkLibrary` v kontextu každého modulu, který ho bude používat. `AfxOleInitModule` vytvoří objekt `CDynLinkLibrary` v regulárním kontextu knihovny MFC DLL tak, aby byl připojen do `CDynLinkLibrary`ho řetězu objektů běžné knihovny MFC DLL.

Pokud vytváříte ovládací prvek OLE a používáte `COleControlModule`, neměli byste volat `AfxOleInitModule`, protože členská funkce `InitInstance` pro `COleControlModule` volá `AfxOleInitModule`.

### <a name="requirements"></a>Požadavky

**Header**: \<AFXDLL_. h >

## <a name="afxnetinitmodule"></a>AfxNetInitModule

Pro podporu soketů MFC z běžné knihovny MFC DLL, která je dynamicky propojena s knihovnou MFC, přidejte volání této funkce ve vaší běžné knihovně MFC DLL `CWinApp::InitInstance` funkce pro inicializaci knihovny MFC Sockets DLL.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Poznámky

Knihovna MFC Sockets DLL je rozšiřující knihovna MFC DLL; aby knihovna DLL rozšíření knihovny MFC mohla být zapojená do `CDynLinkLibrary`ho řetězce, musí vytvořit objekt `CDynLinkLibrary` v kontextu každého modulu, který ho bude používat. `AfxNetInitModule` vytvoří objekt `CDynLinkLibrary` v regulárním kontextu knihovny MFC DLL tak, aby byl připojen do `CDynLinkLibrary`ho řetězu objektů běžné knihovny MFC DLL.

### <a name="requirements"></a>Požadavky

**Header:** \<AFXDLL_. h >

## <a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Pomocí této funkce lze získat aktuální stav příznaku stavu pro jednotlivé moduly, který má vliv na WinSxS chování knihovny MFC.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota příznaku stavu modulu

### <a name="remarks"></a>Poznámky

Když je nastaven příznak (což je výchozí nastavení) a vlákno vstoupí do modulu MFC (viz [AFX_MANAGE_STATE](#afx_manage_state)), je aktivován kontext modulu.

Pokud příznak není nastaven, kontext modulu není aktivován při zadání.

Kontext modulu je určen z jeho manifestu, obvykle je integrován do prostředků modulů.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcomctl32. h

## <a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState

Voláním této funkce nastavíte stav modulu před inicializací a/nebo pro obnovení předchozího stavu modulu po vyčištění.

### <a name="syntax"></a>Syntaxe

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu `AFX_MODULE_STATE`.

### <a name="remarks"></a>Poznámky

Struktura `AFX_MODULE_STATE` obsahuje globální data pro modul, to znamená část stavu modulu, která je vložena nebo vyjmuta.

Ve výchozím nastavení používá knihovna MFC popisovač prostředků hlavní aplikace pro načtení šablony prostředku. Pokud máte exportovanou funkci v knihovně DLL, jako je například jedna, která spustí dialogové okno v knihovně DLL, tato šablona je ve skutečnosti uložena v modulu knihovny DLL. Aby bylo možné použít správný popisovač, je nutné přepnout stav modulu. To lze provést přidáním následujícího kódu na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Tím se zahodí aktuální stav modulu se stavem vráceným z `AfxGetStaticModuleState` až do konce aktuálního oboru.

Další informace o stavech modulů a knihovně MFC naleznete v tématu "Správa údajů o stavu modulů knihovny MFC" v tématu [vytváření nových dokumentů, oken a zobrazení](../creating-new-documents-windows-and-views.md) a [technické poznámky 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxstat_. h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Voláním této funkce v knihovně DLL rozšíření MFC `DllMain` k inicializaci knihovny DLL.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Odkaz na strukturu [struktury AFX_EXTENSION_MODULE](afx-extension-module-structure.md) , která bude obsahovat stav modulu DLL rozšíření MFC po inicializaci. Stav obsahuje kopii objektů běhové třídy, které byly inicializovány knihovnou DLL knihovny MFC jako součást normálního vytváření statických objektů před zadáním `DllMain`.

*hModule*<br/>
Popisovač modulu DLL rozšíření MFC.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je rozšiřující knihovna MFC DLL úspěšně inicializována; v opačném případě FALSE.

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

`AfxInitExtensionModule` vytvoří kopii HMODULE knihovny DLL a zachytává běhové třídy DLL (`CRuntimeClass` struktury) a také její objekty objektů (`COleObjectFactory` objektů) pro pozdější použití při vytváření objektu `CDynLinkLibrary`.
Knihovny DLL rozšíření MFC musí ve své `DllMain` funkci provádět dvě věci:

- Zavolejte [AfxInitExtensionModule](#afxinitextensionmodule) a podívejte se na vrácenou hodnotu.

- Vytvořte objekt `CDynLinkLibrary`, pokud bude knihovna DLL exportovat objekty [struktury CRuntimeClass](cruntimeclass-structure.md) nebo má vlastní prostředky.

Můžete volat `AfxTermExtensionModule` pro vyčištění rozšiřující knihovny MFC DLL, když se každý proces odpojí od rozšiřující knihovny MFC DLL (která se stane, když se proces ukončí nebo když je knihovna DLL uvolněna jako výsledek volání `AfxFreeLibrary`).

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDLL_. h

## <a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Pomocí této funkce lze nastavit příznak stavu pro jednotlivé moduly, který má vliv na WinSxS chování knihovny MFC.

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
Nová hodnota příznaku stavu modulu

### <a name="remarks"></a>Poznámky

Když je nastaven příznak (což je výchozí nastavení) a vlákno vstoupí do modulu MFC (viz [AFX_MANAGE_STATE](#afx_manage_state)), je aktivován kontext modulu.
Pokud příznak není nastaven, kontext modulu není aktivován při zadání.
Kontext modulu je určen z jeho manifestu, obvykle je integrován do prostředků modulů.

### <a name="example"></a>Příklad

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxcomctl32. h

## <a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Voláním této funkce umožníte knihovně MFC vyčistit knihovnu DLL rozšíření MFC, když se každý proces odpojí od knihovny DLL (což se stane, když se proces ukončí, nebo když je knihovna DLL uvolněna jako výsledek volání `AfxFreeLibrary`).

### <a name="syntax"></a>Syntaxe

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parametry

*státech*<br/>
Odkaz na strukturu [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) , která obsahuje stav modulu DLL rozšíření MFC.

*Koule*<br/>
Je-li nastavena hodnota TRUE, vyčistěte všechny moduly DLL rozšíření MFC. V opačném případě vyčistěte pouze aktuální modul knihovny DLL.

### <a name="remarks"></a>Poznámky

`AfxTermExtensionModule` odstraní všechna místní úložiště připojená k modulu a odstraní všechny položky z mezipaměti mapování zpráv. Příklad:

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

Pokud vaše aplikace načítá a uvolňuje knihovny DLL rozšíření MFC dynamicky, nezapomeňte volat `AfxTermExtensionModule`. Vzhledem k tomu, že většina rozšiřujících knihoven DLL knihovny MFC není dynamicky načítána (obvykle jsou propojena prostřednictvím jejich knihoven importu), volání `AfxTermExtensionModule` obvykle není nutné.

Knihovny DLL rozšíření MFC musí volat [AfxInitExtensionModule](#afxinitextensionmodule) v jejich `DllMain`. Pokud bude knihovna DLL exportovat objekty [CRuntimeClass](cruntimeclass-structure.md) nebo má vlastní prostředky, je nutné také vytvořit objekt `CDynLinkLibrary` v `DllMain`.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFXDLL_. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Správa údajů o stavu modulů knihovny MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
