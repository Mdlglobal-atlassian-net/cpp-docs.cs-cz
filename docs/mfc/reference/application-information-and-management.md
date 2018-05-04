---
title: Informace o aplikaci a správu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54265814b4b60b08bed780a39ecadcace3242202
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="application-information-and-management"></a>Informace o aplikacích a správa aplikací
Když píšete aplikaci, můžete vytvořit jeden [CWinApp](../../mfc/reference/cwinapp-class.md)-odvozené objektu. V některých případech můžete chtít získat informace o tomto objektu z mimo `CWinApp`-odvozené objektu. Nebo může potřebovat přístup k ostatním objektům globální "Manager".
  
 Knihovny Microsoft Foundation Class poskytuje následující funkce globální můžete provést tyto úlohy:  
  
### <a name="application-information-and-management-functions"></a>Informace o aplikaci a funkce správy  
  
|||  
|-|-|  
|[AfxBeginThread –](#afxbeginthread)|Vytvoří nové vlákno.|  
|[Afxcontextmenumanager –](#afxcontextmenumanager)|Ukazatel na globální [kontextové nabídky manager](ccontextmenumanager-class.md).|
|[AfxEndThread –](#afxendthread)|Ukončí aktuální vlákno.|  
|[AfxFindResourceHandle –](#afxfindresourcehandle)|Provede řetězu prostředků a vyhledat konkrétní ID prostředků pomocí prostředku a typ prostředku. |
|[AfxFreeLibrary](#afxfreelibrary)|Snižuje počet odkaz na modul načíst dynamická knihovna (DLL); Pokud počet odkazů hodnota nula, nenamapovaný modul.|  
|[AfxGetApp –](#afxgetapp)|Vrátí ukazatel na aplikaci je jeden `CWinApp` objektu.|  
|[Afxgetappname –](#afxgetappname)|Vrátí řetězec, který obsahuje název aplikace.|  
|[Afxgetinstancehandle –](#afxgetinstancehandle)|Vrátí `HINSTANCE` představující tuto instanci aplikace.|  
|[Afxgetmainwnd –](#afxgetmainwnd)|Vrací ukazatel na aktuální "hlavní" okno aplikace, bez OLE nebo okno rámečkem na místě serverová aplikace.|  
|[Afxgetperuserregistration –](#afxgetperuserregistration)|Tato funkce slouží k určení, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|  
|[AfxGetResourceHandle –](#afxgetresourcehandle)|Vrátí `HINSTANCE` ke zdroji výchozí prostředky aplikace. Použijte pro přístup k prostředkům aplikace přímo.|  
|[Afxgetthread –](#afxgetthread)|Načte ukazatel na aktuální [CWinThread](../../mfc/reference/cwinthread-class.md) objektu.|  
|[Afxinitrichedit –](#afxinitrichedit)|Inicializuje verze, že ovládací prvek pro aplikace pro úpravy s formátováním 1.0.|  
|[Afxinitrichedit2 –](#afxinitrichedit2)|Inicializuje verze, že ovládací prvek pro aplikace pro úpravy s formátováním 2.0 nebo novější.| 
|[Afxisextendedframeclass –](#afxisextendedframeclass)|Určuje, zda je daný okna objekt rozšířeného rámce.|
|[Afxismfctoolbar –](#afxismfctoolbar)|Určuje, zda je daný okna objekt panelu nástrojů.|
|[Afxkeyboardmanager –](#afxkeyboardmanager)|Ukazatel na globální [klávesnice manager](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Mapuje modulu DLL a vrátí popisovač, který slouží k získávání adresy funkce knihovny DLL.|  
|[Afxmenutearoffmanager –](#afxmenutearoffmanager)|Ukazatel na globální [manager nabídky odtržení](cmenutearoffmanager-class.md).|
|[Afxmousemanager –](#afxmousemanager)|Ukazatel na globální [manager myši](cmousemanager-class.md).|
|[Afxregisterclass –](#afxregisterclass)|Zaregistruje třídu okna v knihovně DLL, která používá MFC.|  
|[Afxregisterwndclass –](#afxregisterwndclass)|Zaregistruje třídu okna Windows doplňují akce automaticky registrovaných MFC.|  
|[Afxsetperuserregistration –](#afxsetperuserregistration)|Nastaví, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** ( **HKCU**) uzlu.|  
|[Afxsetresourcehandle –](#afxsetresourcehandle)|Nastaví `HINSTANCE` popisovač, kde jsou načtena výchozí prostředky aplikace.|  
|[Afxshellmanager –](#afxshellmanager)|Ukazatel na globální [shell manager](cshellmanager-class.md). |
|[Afxsocketinit –](#afxsocketinit)|Volá se `CWinApp::InitInstance` přepsání inicializovat sokety systému Windows.|  
|[Afxusertoolsmanager –](#afxusertoolsmanager)|Ukazatel na globální [nástroje Správce uživatelů](cusertoolsmanager-class.md).|
|[Afxwininit –](#afxwininit)|Voláno rozhraním MFC zadané `WinMain` funkce, jako součást [CWinApp](../../mfc/reference/cwinapp-class.md) inicializace aplikace využívající grafické rozhraní, k chybě při inicializaci MFC. Je nutné volat přímo pro konzolové aplikace, které používají MFC.|  
  

  
##  <a name="afxbeginthread"></a>  AfxBeginThread –  
 Volání této funkce vytvořit nové vlákno.  
  
```   
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,  
    LPVOID pParam,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `pfnThreadProc`  
 Odkazuje na funkci řízení pro pracovní vlákno. Nemůže být **NULL**. Tato funkce musí být deklarován takto:  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 RUNTIME_CLASS objektu odvozené od [CWinThread](../../mfc/reference/cwinthread-class.md).  
  
 *pParam*  
 Parametr předaný funkci řízení jak je uvedené v parametru v deklaraci funkce `pfnThreadProc`.  
  
 `nPriority`  
 Požadovaná priorita vlákna. Úplný seznam a popis dostupných priority najdete v tématu [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) ve Windows SDK.  
  
 `nStackSize`  
 Určuje velikost v bajtech zásobníku pro nové vlákno. Pokud je 0, výchozí velikost zásobníku stejná velikost zásobníku jako vytváření vláken.  
  
 `dwCreateFlags`  
 Určuje další příznak, který řídí vytváření vlákno. Tento příznak může obsahovat jednu ze dvou hodnot:  
  
- **CREATE_SUSPENDED** vlákno začínat pozastavit započítává jako jeden. Použití **CREATE_SUSPENDED** Pokud chcete k inicializaci dat člena z `CWinThread` objektů, jako například [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) nebo žádné členy vaší odvozené třídy, než je vlákno spuštění. Po dokončení vaší inicializace použít [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) spustit vlákno spuštěna. Dokud nebude spustit vlákno `CWinThread::ResumeThread` je volána.  
  
- **0** spustit vlákno ihned po vytvoření.  
  
 `lpSecurityAttrs`  
 Odkazuje na [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) struktura, která určuje atributy zabezpečení pro vlákno. Pokud **NULL**, stejné zabezpečení atributy, jako je vytváření vláken se použije. Další informace o tuto strukturu najdete v části Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený vlákno objekt, nebo **NULL** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 První formu `AfxBeginThread` vytvoří pracovní vlákno. Druhý formulář vytvoří vlákno, které může sloužit jako vlákna uživatelského rozhraní nebo jako pracovní vlákno.  
  
 `AfxBeginThread` Vytvoří novou `CWinThread` objektu, volání jeho [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funkci, aby se spustí provádění vlákna a vrací ukazatel na vlákno. Kontroly se provádějí v celém procesu zajistit, že všechny objekty jsou deallocated správně má libovolná součást vytvoření selhat. Chcete-li ukončit vlákno, volejte [AfxEndThread –](#afxendthread) z v rámci přístup z více vláken, nebo return z řídící funkce pracovní vlákno.  
  
 Multithreading musí být povolen v aplikaci; Tuto funkci, jinak nebude úspěšná. Další informace o povolení více vláken, najdete v části [/MD, / MT, /LD (použít běhovou knihovnu)](../../build/reference/md-mt-ld-use-run-time-library.md) pod *Visual C++ – možnosti kompilátoru*.  
  
 Další informace o `AfxBeginThread`, najdete v článcích [Multithreading: vytváření pracovních vláken](../../parallel/multithreading-creating-worker-threads.md) a [Multithreading: vytváření vláken uživatelského rozhraní](../../parallel/multithreading-creating-user-interface-threads.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  

## <a name="afxcontextmenumanager"></a> Afxcontextmenumanager –
Ukazatel na globální [kontextové nabídky manager](ccontextmenumanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcontextmenumanager.h     

### <a name="see-also"></a>Viz také   
 [CContextMenuManager – třída](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>  AfxEndThread –  
 Volání této funkce na ukončení aktuálně spuštěných vláken.  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>Parametry  
 *nExitCode*  
 Určuje kód ukončení vlákna.  
  
 *bDelete*  
 Odstraní objekt vlákna z paměti.  
  
### <a name="remarks"></a>Poznámky  
 Musí být volat z vlákna ukončena.  
  
 Další informace o `AfxEndThread`, najdete v článku [Multithreading: ukončení vláken](../../parallel/multithreading-terminating-threads.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Použití `AfxFindResourceHandle` provede řetězu prostředků a vyhledat konkrétní typ ID a prostředků prostředků pomocí prostředků.  
   
### <a name="syntax"></a>Syntaxe    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Ukazatel na řetězec obsahující ID prostředku.    
 *lpszType*  
 Ukazatel na typ prostředku. Seznam typů prostředků najdete v tématu [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) ve Windows SDK.  
   
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro modul, který obsahuje prostředek.  
   
### <a name="remarks"></a>Poznámky  
 `AfxFindResourceHandle` Vyhledá konkrétní prostředek a vrátí popisovač modul, který obsahuje prostředek. Prostředek může být v rozšíření MFC DLL načtený. `AfxFindResourceHandle` informuje, která má prostředku.  
  
 Moduly jsou prohledávány v tomto pořadí:  
  
1.  Hlavní modulu (Pokud se jedná MFC – rozšiřující knihovny DLL).  
  
2.  Moduly non systému.  
  
3.  Moduly pro konkrétní jazyk.  
  
4.  Hlavní modulu (Pokud je systémová knihovna DLL).  
  
5.  Moduly System.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>  AfxFreeLibrary  
 Obě `AfxFreeLibrary` a `AfxLoadLibrary` udržovat počet odkazů pro každý modul načíst knihovny.  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstLib*  
 Obslužná rutina modulu načíst knihovny. [AfxLoadLibrary](#afxloadlibrary) vrátí tento popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud funkce proběhne úspěšně, jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 `AfxFreeLibrary` snižuje počet odkaz na modul načíst dynamická knihovna (DLL). Když počet odkazů hodnota nula, modul nenamapovaný z adresního prostoru volajícího procesu a popisovač již není platný. Tento počet odkazů se zvýší pokaždé, když `AfxLoadLibrary` je volána.  
  
 Před zrušení mapování modulu knihovny, umožňuje systém knihovnu DLL k odpojení od procesy použití. Díky tomu dává příležitost k vyčištění prostředků přidělené jménem aktuální proces knihovnu DLL. Po vstupní bod funkce vrátí hodnotu, modul knihovny odebrán z adresního prostoru aktuálního procesu.  
  
 Použití `AfxLoadLibrary` pro mapování modulu DLL.  
  
 Nezapomeňte použít `AfxFreeLibrary` a `AfxLoadLibrary` (místo funkce Win32 **FreeLibrary** a **LoadLibrary**) Pokud vaše aplikace používá více vláken. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když MFC – rozšiřující knihovny DLL je načítání a uvolňování nejsou poškozeny globální stav MFC.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [AfxLoadLibrary](#afxloadlibrary).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdll_.h  
  
##  <a name="afxgetapp"></a>  AfxGetApp –  
 Ukazatele, vrátí tato funkce slouží pro přístup k aplikaci informace, jako je hlavní odeslání zpráv kód nebo okně nejhornější.  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na hodnotu single `CWinApp` objekt pro aplikaci.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda vrátí hodnotu NULL, může to znamenat, že hlavní okno aplikace ještě nebyla inicializována plně. Je také může znamenat problém.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxgetappname"></a>  Afxgetappname –  
 Řetězec vrácený pomocí této funkce lze pro diagnostické zprávy nebo jako kořenové pro dočasné řetězec názvy.  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukončené hodnotou null řetězec obsahující název aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>  Afxgetinstancehandle –  
 Tato funkce umožňuje načíst popisovač instance aktuální aplikace.  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HINSTANCE` Na aktuální instanci aplikace. Pokud je volána v rámci knihovny DLL propojené s USRDLL verze knihovny MFC, `HINSTANCE` na knihovnu DLL je vrácen.  
  
### <a name="remarks"></a>Poznámky  
 `AfxGetInstanceHandle` vždy vrátí hodnotu `HINSTANCE` spustitelného souboru (. Soubor EXE) Pokud je volána v rámci s verzí USRDLL MFC propojené knihovny DLL. V takovém případě se vrátí `HINSTANCE` na knihovnu DLL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxgetmainwnd"></a>  Afxgetmainwnd –  
 Pokud je aplikace serveru OLE, volejte tuto funkci k získání ukazatele na aktivní hlavní okno aplikace místo přímo odkazující na [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) členem objektu application.  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud má server objekt, který je na místě aktivní uvnitř kontejneru a tento kontejner je aktivní, tato funkce vrací ukazatel na rámec okna objekt, který obsahuje aktivní dokument na místě.  
  
 Pokud se žádný objekt, který je na místě aktivní do kontejneru, nebo aplikaci není OLE server, jednoduše vrátí tato funkce `m_pMainWnd` objektu aplikace.  
  
 Pokud `AfxGetMainWnd` je volána z vlákna primární aplikace, vrátí hlavní okno aplikace podle výše uvedených pravidel. Pokud je tato funkce volána z jiného vlákna v aplikaci, funkce vrátí hodnotu hlavního okna přidružené vláken, který vytvořil volání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace není OLE server, pak volání této funkce je ekvivalentní přímo odkazující na `m_pMainWnd` členem aplikační objekt.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>  Afxgetperuserregistration –  
 Tato funkce slouží k určení, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** ( **HKCU**) uzlu.  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Označuje, že se přesměruje informace o registru **HKCU** uzlu; `FALSE` označuje, že aplikace do uzlu výchozí zapisuje informace registru. Je výchozí uzel **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Poznámky  
 Pokud povolíte registru přesměrování, rozhraní přesměruje přístup z **HKCR** k **HKEY_CURRENT_USER\Software\Classes**. Přesměrování se týká pouze rozhraní MFC a knihovna ATL.  
  
 Pokud chcete změnit, zda aplikace přesměruje přístup k registru, použijte [afxsetperuserregistration –](#afxsetperuserregistration).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle –  
 Použití `HINSTANCE` popisovač vrácený pomocí této funkce pro přístup k prostředkům aplikace přímo, například ve volání funkce systému Windows **FindResource**.  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `HINSTANCE` Popisovač, kde jsou načtena výchozí prostředky aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxgetthread"></a>  Afxgetthread –  
 Volání této funkce můžete získat ukazatel [CWinThread](../../mfc/reference/cwinthread-class.md) objekt reprezentující aktuálně prováděné vlákno.  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktuálně prováděné podprocesu. v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Musí být volána z požadované vlákna.  
  
> [!NOTE]
>  Pokud provádíte přenos volání projektu knihovny MFC `AfxGetThread` z Visual C++ verze 4.2, 5.0 nebo 6.0, `AfxGetThread` volání [AfxGetApp](#afxgetapp) Pokud se nenajde žádný přístup z více vláken. V novějších verzích kompilátoru `AfxGetThread` vrátí **NULL** Pokud nebyl nalezen žádný přístup z více vláken. Pokud chcete, aby vlákno aplikace, musí volat `AfxGetApp`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxinitrichedit"></a>  Afxinitrichedit –  
 Volání této funkce se inicializovat ovládací prvek RichEdit (verze 1.0) pro aplikaci.  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je poskytována z důvodu zpětné kompatibility. Nové aplikace by měly používat [afxinitrichedit2 –](#afxinitrichedit2).  
  
 `AfxInitRichEdit` načte RICHED32. Knihovny DLL k chybě při inicializaci verzi ovládacího prvku RichEdit 1.0. Použití verze 2.0 a 3.0 bohatých ovládacích prvků pro úpravy, RICHED20. Knihovna DLL je třeba načíst. Toho dosahuje pomocí volání [afxinitrichedit2 –](#afxinitrichedit2).  
  
 Chcete-li aktualizovat ovládacích prvcích pro úpravy bohaté v existujících aplikací Visual C++ na verzi 2.0, otevřete. RC soubor jako text, změnit název třídy každý bohatých ovládacích prvků pro úpravy z "RICHEDIT" na "RichEdit20a". Potom můžete nahradit volání `AfxInitRichEdit` s `AfxInitRichEdit2`.  
  
 Tato funkce také inicializuje knihovnu běžné ovládací prvky, pokud knihovně již nebyla inicializována pro proces. Pokud používáte prvku RichEdit přímo z aplikace MFC, by měly volat tuto funkci, aby zajistil, že MFC byla správně inicializována runtime ovládacího prvku RichEdit. Když zavoláte metodu Create z [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview –](../../mfc/reference/cricheditview-class.md), nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle nemusíte volání této funkce, ale v některých případech může být nezbytné.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxinitrichedit2"></a>  Afxinitrichedit2 –  
 Volání této funkce se inicializovat ovládací prvek RichEdit (verze 2.0 a novější) pro aplikaci.  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce RICHED20 načíst. Knihovny DLL a inicializovat verze 2.0 bohaté ovládacích prvků pro úpravy. Když zavoláte metodu Create z [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [cricheditview –](../../mfc/reference/cricheditview-class.md), nebo [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), obvykle nemusíte volání této funkce, ale v některých případech může být nezbytné.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  

  ## <a name="afxisextendedframeclass"></a>  Afxisextendedframeclass –
Určuje, zda je daný okna objekt rozšířeného rámce.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>Parametry  
 [v] `pWnd`  
 Ukazatel na objekt, který je odvozený od `CWnd`.  
   
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je okno zadaný objekt rozšířeného rámce; v opačném případě `FALSE`.  
   
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `TRUE` Pokud `pWnd` je odvozena z jednoho z následujících tříd:  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 Tato metoda je užitečná, když budete muset ověřit, jestli je parametr funkce nebo metoda rozšířené rámci okna aplikace.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  
   
### <a name="see-also"></a>Viz také  
 [Třída CWnd](cwnd-class.md)   
 [CFrameWndEx – třída](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a> Afxismfctoolbar –
Určuje, zda je daný okna objekt panelu nástrojů.  
   
### <a name="syntax"></a>Syntaxe    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>Parametry  
 [v] `pWnd`  
 Ukazatel na objekt, který je odvozený od `CWnd`.  
   
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je okno zadaný objekt na panelu nástrojů v opačném případě `FALSE`.  
   
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `TRUE` Pokud `pWnd` je odvozena z `CMFCToolBar`. Tato metoda je užitečná, když budete muset ověřit, jestli je parametr funkce nebo metoda `CMFCToolBar` objektu.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpriv.h  
   
### <a name="see-also"></a>Viz také  
 [Třída CWnd](cwnd-class.md)   
 [CMFCToolBar – třída](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a> Afxkeyboardmanager –
Ukazatel na globální [klávesnice manager](ckeyboardmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxkeyboardmanager.h  
   
### <a name="see-also"></a>Viz také  

 [Makra, globální funkce a globální proměnné](mfc-macros-and-globals.md)   
 [CKeyboardManager – třída](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary  
 Použití `AfxLoadLibrary` pro mapování modulu DLL.  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>Parametry  
 *lpszModuleName*  
 Odkazuje na řetězec ukončené hodnotou null, který obsahuje název měněného modulu (buď. Knihovny DLL nebo. Soubor EXE). Zadaný název je název modulu.  
  
 Pokud řetězec Určuje cestu, ale soubor v zadaný adresář neexistuje, funkce se nezdaří.  
  
 Pokud cesta není zadána a příponu názvu souboru je vynechán, bude výchozí rozšíření. Knihovna DLL je připojen. Řetězec filename však může zahrnovat koncovou mezeru bodu (.) k označení, že je název modulu žádné rozšíření. Pokud není zadána žádná cesta, funkce hledá soubor v tomto pořadí:  
  
-   Adresář, ze které aplikace načtena.  
  
-   Aktuální adresář.  
  
- **Systém Windows 95/98:** adresář systému Windows. **Systém Windows NT:** adresář systému Windows 32-bit. Název tohoto adresáře je SYSTEM32.  
  
- **Pouze systém Windows NT:** adresář systému Windows 16 bitů. Neexistuje žádná funkce Win32, který získá cestu tohoto adresáře, ale je prohledána. Název tohoto adresáře je systém.  
  
-   Adresář systému Windows.  
  
-   Adresáře, které jsou uvedeny v proměnné prostředí PATH.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, je vrácenou hodnotu popisovač pro modul. Pokud se funkce nezdaří, je vrácenou hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí popisovač, který lze použít v [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) získat adresu funkce knihovny DLL. `AfxLoadLibrary` Můžete také použít k mapování z ostatních modulů spustitelný soubor.  
  
 Každý proces udržuje počet odkazů pro každý modul načíst knihovny. Tento počet odkazů se zvýší pokaždé, když `AfxLoadLibrary` se nazývá a se odečte pokaždé, když `AfxFreeLibrary` je volána. Když počet odkazů hodnota nula, modul nenamapovaný z adresního prostoru volajícího procesu a popisovač již není platný.  
  
 Nezapomeňte použít `AfxLoadLibrary` a `AfxFreeLibrary` (místo funkce Win32 **LoadLibrary** a **FreeLibrary**) Pokud vaše aplikace používá více vláken a dynamicky načtenou knihovny MFC rozšiřující knihovny DLL. Pomocí `AfxLoadLibrary` a `AfxFreeLibrary` zajistí, že spuštění a vypnutí kód, který provede, když je rozšíření MFC DLL načítání a uvolňování nejsou poškozeny globální stav MFC.  
  
 Pomocí `AfxLoadLibrary` v aplikaci vyžaduje, abyste dynamicky propojit DLL verze knihovny MFC; v záhlaví souboru `AfxLoadLibrary`, Afxdll_.h, je pouze pokud MFC je propojena s aplikací jako knihovny DLL zahrnuty. Toto je záměrné, protože budete muset propojit DLL verze knihovny MFC použít nebo vytvořit MFC – rozšiřující knihovny DLL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a> Afxmenutearoffmanager –
Ukazatel na globální [manager nabídky odtržení](cmenutearoffmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>Viz také     
 [CMenuTearOffManager – třída](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>  Afxmousemanager –
Ukazatel na globální [manager myši](cmousemanager-class.md).  
   
### <a name="syntax"></a>Syntaxe  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmousemanager.h  
   
### <a name="see-also"></a>Viz také  
 [CMouseManager – třída](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>  Afxregisterclass –  
 Pomocí této funkce můžete zaregistrovat třídy oken v knihovně DLL, která používá MFC.  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>Parametry  
 *lpWndClass*  
 Ukazatel na [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura obsahující informace o třídě okno k registraci. Další informace o tuto strukturu najdete v části Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud třída je úspěšně registrovaná; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte tuto funkci, třída je automaticky registrace po odpojen knihovnu DLL.  
  
 V sestavení pro – knihovny DLL `AfxRegisterClass` identifikátor je definován jako makra, která se mapuje na funkce systému Windows **RegisterClass**, protože jsou automaticky registrace třídy registrované v aplikaci. Pokud používáte `AfxRegisterClass` místo **RegisterClass**, může být použit bez změn v aplikaci a v knihovně DLL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxregisterwndclass"></a>  Afxregisterwndclass –  
 Umožňuje registrovat vlastní třídy oken.  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>Parametry  
 *nClassStyle*  
 Určuje styl třídy systému Windows nebo kombinaci stylů, vytvořené pomocí bitové operace OR ( **&#124;**) operátor pro třídu oken. Seznam třída styly najdete v tématu [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura ve Windows SDK. Pokud **NULL**, výchozí hodnoty bude nastavena takto:  
  
-   Nastaví styl myši na **CS_DBLCLKS**, které odesílá poklikejte na zprávy do okna postupu při poklepání myší.  
  
-   Nastaví styl šipky kurzor na Windows standard **IDC_ARROW**.  
  
-   Nastaví štětec pozadí plochy **NULL**, takže okno nebude vymazat jeho pozadí.  
  
-   Nastaví na ikonu na ikonu s logem Windows standard, s připravenými příznak.  
  
 `hCursor`  
 Určuje popisovač pro prostředek kurzoru být nainstalovaný v každé okna vytvořeného z okna třídy. Pokud použijete výchozí **0**, zobrazí se standardní **IDC_ARROW** kurzoru.  
  
 *hbrBackground*  
 Určuje popisovač pro prostředek štětce být nainstalovaný v každé okna vytvořeného z okna třídy. Pokud použijete výchozí **0**, budete mít **NULL** štětec pozadí plochy a vaše bude okno, ve výchozím nastavení, nelze vymazat jeho pozadí při zpracování [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055).  
  
 `hIcon`  
 Určuje popisovač pro prostředek ikonu být nainstalovaný v každé okna vytvořeného z okna třídy. Pokud použijete výchozí **0**, zobrazí se ikona standardní, s připravenými příznak logo systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukončené hodnotou null řetězec obsahující název třídy. Můžete předat tento název třídy a **vytvořit** – členská funkce v `CWnd` či jiné **CWnd -** odvozených tříd se vytvořit okno. Název je vytvořen pomocí knihovny Microsoft Foundation Class.  
  
> [!NOTE]
>  Vrácená hodnota je ukazatel na statické vyrovnávací paměti. Pokud chcete uložit tento řetězec, je přiřadit `CString` proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Knihovny Microsoft Foundation Class automaticky zaregistruje několik tříd standardní okno. Pokud chcete zaregistrovat vlastní třídy oken, volání této funkce.  
  
 Název zaregistrovat pro třídu podle `AfxRegisterWndClass` závisí výhradně na parametry. Když zavoláte `AfxRegisterWndClass` vícekrát s identické parametry pouze registraci třídu při prvním volání. Následující volání `AfxRegisterWndClass` s identické parametry jednoduše vrátit classname již zaregistrován.  
  
 Když zavoláte `AfxRegisterWndClass` víc tříd CWnd odvozené s identické parametry, místo získávání třídu samostatném okně pro každou třídu, každá třída sdílí stejnou třídu oken. To může způsobit problémy, pokud **CS_CLASSDC** styl třída se používá. Místo více **CS_CLASSDC** třídy oken, skončili s jedním **CS_CLASSDC** okno třídy a všechny systémy windows C++, které používají, že třída sdílet stejný řadič domény. Chcete-li se tomuto problému vyhnout, volejte [afxregisterclass –](#afxregisterclass) zaregistrovat tuto třídu.  
  
 Technická poznámka naleznete [TN001: registrace tříd oken](../../mfc/tn001-window-class-registration.md) Další informace o registrace tříd oken a `AfxRegisterWndClass` funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>  Afxsetperuserregistration –  
 Nastaví, zda aplikace přesměruje registru přístup k **HKEY_CURRENT_USER** ( **HKCU**) uzlu.  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `bEnable`  
 `TRUE` Označuje, že se přesměruje informace o registru **HKCU** uzlu; `FALSE` označuje, že aplikace do uzlu výchozí zapisuje informace registru. Je výchozí uzel **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Poznámky  

Před Windows Vista, aplikace, které získat přístup k registru obvykle používají **HKEY_CLASSES_ROOT** uzlu. S Windows Vista nebo novější operační systémy, musí však spuštění aplikace, v režimu zvýšených oprávnění k zápisu do **HKCR**.  
  
 Tato metoda umožňuje aplikaci číst a zapisovat do registru bez spuštění v režimu se zvýšenou přesměrováním registru přístup z **HKCR** k **HKCU**. Další informace najdete v tématu [stránky vlastností Linkeru](../../ide/linker-property-pages.md).  
  
 Pokud povolíte registru přesměrování, rozhraní přesměruje přístup z **HKCR** k **HKEY_CURRENT_USER\Software\Classes**. Přesměrování se týká pouze rozhraní MFC a knihovna ATL.  
  
 Výchozí implementace přistupuje ke klíči registru **HKCR**.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>  Afxsetresourcehandle –  
 Pomocí této funkce můžete nastavit `HINSTANCE` obslužná rutina, která určuje, kde jsou načteny výchozí prostředky aplikace.  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>Parametry  
 `hInstResource`  
 Popisovač modul nebo instance. Soubor EXE nebo DLL ze které jsou načtena prostředky aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  

## <a name="afxshellmanager"></a>  Afxshellmanager –
Ukazatel na globální [shell manager](cshellmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxshellmanager.h  
   
### <a name="see-also"></a>Viz také  
 [CShellManager – třída](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>  Afxsocketinit –  
 Volání této funkce vašem `CWinApp::InitInstance` přepsání inicializovat sokety systému Windows.  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>Parametry  
 `lpwsaData`  
 Ukazatel [wsadata –](../../mfc/reference/wsadata-structure.md) struktura. Pokud `lpwsaData` se nerovná `NULL`, pak na adresu `WSADATA` struktura vyplní volání `WSAStartup`. Tato funkce taky zajišťuje, že `WSACleanup` je volána pro vás předtím, než se aplikace ukončí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je funkce úspěšná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte MFC sockets v sekundární vláken v staticky propojené knihovny MFC aplikaci, musí volat `AfxSocketInit` v každé vlákno, která používá sockets k chybě při inicializaci knihovny soketů. Ve výchozím nastavení `AfxSocketInit` je volán jen v primárních vlákno.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxsock.h  

## <a name="afxusertoolsmanager"></a>  Afxusertoolsmanager –
Ukazatel na globální [nástroje Správce uživatelů](cusertoolsmanager-class.md).  
   
### <a name="syntax"></a>Syntaxe    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxusertoolsmanager.h  
   
### <a name="see-also"></a>Viz také  
 [CUserToolsManager – třída](cusertoolsmanager-class.md)
 
  
##  <a name="afxwininit"></a>  Afxwininit –  
 Tato funkce je volána pomocí zadané MFC `WinMain` funkce, jako součást [CWinApp](../../mfc/reference/cwinapp-class.md) inicializace aplikace využívající grafické rozhraní, k chybě při inicializaci MFC.  
  
```  
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,  
    HINSTANCE hPrevInstance,  
    LPTSTR lpCmdLine,  
    int nCmdShow);  
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Obslužná rutina modulu aktuálně spuštěná.  
  
 *hPrevInstance*  
 Popisovač pro předchozí instanci aplikace. Pro aplikaci na základě Win32, tento parametr je vždy **NULL**.  
  
 `lpCmdLine`  
 Odkazuje na řetězec ukončené hodnotou null určující příkazového řádku pro aplikaci.  
  
 `nCmdShow`  
 Určuje, jak by být zobrazena v hlavním okně grafického uživatelského rozhraní aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Pro konzolovou aplikaci, která nepoužívá MFC zadané `WinMain` funkce, musí volat `AfxWinInit` přímo k chybě při inicializaci MFC.  
  
 Když zavoláte `AfxWinInit` sami, by měly deklarovat instanci `CWinApp` třídy. Pro aplikaci konzoly, můžete zvolit není odvozena vlastní třídy z `CWinApp` a místo toho použít instanci `CWinApp` přímo. Tento postup je vhodné, pokud se rozhodnete ponechat všechny funkce pro vaši aplikaci ve vaší implementace nástroje **hlavní**.  
  
> [!NOTE]
>  Při vytváření kontextu aktivace pro sestavení, používá MFC prostředku manifestu poskytované modulem uživatele. Aktivační kontext je vytvořen v `AfxWinInit`. Další informace najdete v tématu [podpora kontextů aktivace ve stavu modulu MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxwin.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp – třída](../../mfc/reference/cwinapp-class.md)
