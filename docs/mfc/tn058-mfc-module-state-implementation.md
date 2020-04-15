---
title: 'TN058: Implementace stavu modulu MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366612"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementace stavu modulu MFC

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato technická poznámka popisuje implementaci konstrukcí stavu modulu knihovny MFC. Pochopení implementace stavu modulu je důležité pro použití knihovny MFC sdílené knihovny DLL z knihovny DLL (nebo OLE v procesu).

Před přečtením této poznámky naleznete v části Správa stavových dat modulů knihovny MFC při [vytváření nových dokumentů, systému Windows a zobrazení](../mfc/creating-new-documents-windows-and-views.md). Tento článek obsahuje důležité informace o použití a přehled informací na toto téma.

## <a name="overview"></a>Přehled

Existují tři druhy informací o stavu knihovny MFC: Stav modulu, Stav procesu a Stav vlákna. Někdy tyto typy stavů mohou být kombinovány. Například mapy popisovače knihovny MFC jsou místní modul a místní vlákno. To umožňuje dva různé moduly mít různé mapy v každém z jejich podprocesů.

Stav procesu a Stav vlákna jsou podobné. Tyto datové položky jsou věci, které byly tradičně globální proměnné, ale musí být specifické pro daný proces nebo vlákno pro správnou podporu Win32s nebo pro správnou podporu multithreading. Kategorie daná datová položka se vejde do závisí na této položce a její požadované sémantiky s ohledem na hranice procesu a vlákna.

Stav modulu je jedinečný v tom, že může obsahovat skutečně globální stav nebo stav, který je místní proces nebo místní vlákno. Kromě toho lze rychle přepnout.

## <a name="module-state-switching"></a>Přepínání stavu modulu

Každé vlákno obsahuje ukazatel na stav "aktuální" nebo "aktivní" modul (není divu, že ukazatel je součástí místního stavu vlákna knihovny MFC). Tento ukazatel se změní, když vlákno spuštění projde hranice modulu, jako je například aplikace volající do ole ovládacího prvku nebo knihovny DLL nebo ole ovládací prvek volání zpět do aplikace.

Aktuální stav modulu se `AfxSetModuleState`přepíná voláním . Z větší části se nikdy nebudete zabývat přímo s rozhraním API. Knihovna MFC, v mnoha případech, bude volat za vás `AfxWndProc`(na WinMain, OLE vstupní body, , atd.). To se provádí v libovolné součásti, kterou `WndProc`píšete `WinMain` staticky `DllMain`propojením ve speciálním a speciálním (nebo) který ví, který stav modulu by měl být aktuální. Tento kód můžete vidět při pohledu na DLLMODUL. CPP nebo APPMODUL. CPP v adresáři Knihovny MFC\SRC.

Je vzácné, že chcete nastavit stav modulu a potom jej nenastavit zpět. Většinu času chcete "push" svůj vlastní stav modulu jako aktuální a poté, co jste hotovi, "pop" původní kontext zpět. To se provádí makro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) a `AFX_MAINTAIN_STATE`speciální třídy .

`CCmdTarget`má speciální funkce pro přepínání stavu modulu. Zejména a `CCmdTarget` je kořenová třída používaná pro automatizaci OLE a vstupní body OLE COM. Stejně jako všechny ostatní vstupní bod vystavené systému, tyto vstupní body musí nastavit správný stav modulu. Jak daný `CCmdTarget` vědět, co "správný" stav modulu by měl být odpověď je, že "pamatuje" co "aktuální" stav modulu je, když je konstruován, tak, aby bylo možné nastavit aktuální stav modulu, že "zapamatováno" hodnotu, když je později volána. V důsledku toho stav modulu, ke kterému je daný `CCmdTarget` objekt přidružen, je stav modulu, který byl aktuální, když byl objekt vytvořen. Vezměte jednoduchý příklad načítání serveru INPROC, vytvoření objektu a volání jeho metod.

1. Knihovna DLL je `LoadLibrary`načtena ole pomocí .

1. `RawDllMain`se nazývá jako první. Nastaví stav modulu do stavu známého statického modulu pro dll. Z tohoto `RawDllMain` důvodu je staticky propojena s dll.

1. Konstruktor pro třídu factory přidružené k našemu objektu se nazývá. `COleObjectFactory`je odvozen `CCmdTarget` z a v důsledku toho si pamatuje, ve kterém stavu modulu byl instancied. To je důležité – když je továrna třídy požádána o vytvoření objektů, nyní ví, jaký stav modulu má být aktuální.

1. `DllGetClassObject`je volána k získání třídy factory. Knihovna MFC prohledá seznam tříd, který je přidružen k tomuto modulu, a vrátí jej.

1. `COleObjectFactory::XClassFactory2::CreateInstance`se nazývá. Před vytvořením objektu a jeho vrácením tato funkce nastaví stav modulu do stavu modulu, který byl aktuální v kroku 3 (ten, který byl aktuální při `COleObjectFactory` vytvoření instance). To se provádí uvnitř [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Při vytvoření objektu je také `CCmdTarget` derivace a `COleObjectFactory` stejným způsobem si pamatuje, který stav modulu byl aktivní, tak i tento nový objekt. Nyní objekt ví, na který stav modulu se má přepnout vždy, když je volán.

1. Klient volá funkci objektu OLE COM, `CoCreateInstance` který přijal z jeho volání. Při volání objektu `METHOD_PROLOGUE` se používá k přepnutí stavu modulu stejně jako `COleObjectFactory` dělá.

Jak můžete vidět, stav modulu je šířen z objektu na objekt při jejich vytváření. Je důležité mít správně nastaven stav modulu. Pokud není nastavena, může váš objekt Knihovny DLL nebo COM pracovat špatně s aplikací knihovny MFC, která ji volá, nebo nemusí být schopna najít vlastní prostředky nebo může selhat jinými mizernými způsoby.

Všimněte si, že některé druhy knihovny DLL, konkrétně "Rozšíření knihovny `RawDllMain` MFC" knihovny DLL `RawDllMain`nepřepínají stav modulu v jejich (ve skutečnosti obvykle nemají ani). Důvodem je, že jsou určeny k chovat "jako by" byly skutečně přítomny v aplikaci, která je používá. Jsou do značné míry součástí aplikace, která je spuštěna a je jejich záměrem změnit globální stav této aplikace.

Ole ovládací prvky a další knihovny DLL jsou velmi odlišné. Nechtějí změnit stav volající aplikace; aplikace, která je volá, nemusí být ani aplikace knihovny MFC, a proto nemusí existovat žádný stav, který by bylo možné změnit. To je důvod, proč bylo vynalezeno přepínání stavu modulu.

Pro exportované funkce z dll, jako je například ten, který spustí dialogové okno v dll, je třeba přidat následující kód na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Tím se zamění aktuální stav modulu se stavem vráceným z [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) až do konce aktuálního oboru.

Pokud není použito AFX_MODULE_STATE makro, dojde k problémům s prostředky v knihovnách DLL. Ve výchozím nastavení knihovna MFC používá popisovač prostředků hlavní aplikace k načtení šablony prostředků. Tato šablona je ve skutečnosti uložena v knihovně DLL. Hlavní příčinou je, že informace o stavu modulu knihovny MFC nebyly přepnuty AFX_MODULE_STATE makro. Popisovač prostředku je obnoven ze stavu modulu knihovny MFC. Nepřepnutí stavu modulu způsobí, že nesprávný popisovač prostředku, které mají být použity.

AFX_MODULE_STATE nemusí být vložendo všech funkcí v dll. Například `InitInstance` může být volána kód knihovny MFC v aplikaci bez AFX_MODULE_STATE `InitInstance` protože knihovna `InitInstance` MFC automaticky posune stav modulu před a potom přepne zpět po vrácení. Totéž platí pro všechny obslužné rutiny mapy zpráv. Běžné knihovny DLL knihovny MFC mají ve skutečnosti speciální proceduru hlavního okna, která automaticky přepne stav modulu před směrováním jakékoli zprávy.

## <a name="process-local-data"></a>Zpracovat místní data

Zpracování místních dat by nebylo tak velké obavy, kdyby nebylo obtížnosti modelu DLL Win32s. Ve win32s všechny knihovny DLL sdílet jejich globální data, i když načtevíce více aplikací. To se velmi liší od "skutečné" Win32 DLL datový model, kde každý DLL získá samostatnou kopii svého datového prostoru v každém procesu, který se připojuje k DLL. Chcete-li přidat ke složitosti, data přidělená na haldě v DLL Win32s je ve skutečnosti konkrétní proces (alespoň pokud jde o vlastnictví jde). Zvažte následující data a kód:

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Zvažte, co se stane, pokud je výše uvedený kód umístěn v dll a že DLL je načten dvěma procesy A a B (ve skutečnosti by to mohly být dvě instance stejné aplikace). Volání `SetGlobalString("Hello from A")`. V důsledku toho je paměť `CString` přidělena pro data v kontextu procesu `CString` A. Mějte na paměti, že sama o sobě je globální a je viditelná pro A i B. Nyní B `GetGlobalString(sz, sizeof(sz))`volá . B budou moci zobrazit data, která A set. Důvodem je, že Win32s nenabízí žádnou ochranu mezi procesy, jako je Win32 dělá. To je první problém; v mnoha případech není žádoucí, aby jedna aplikace ovlivnila globální data, která je považována za vlastněná jinou aplikací.

Existují i další problémy. Řekněme, že a nyní odchází. Po ukončení a je paměť používaná řetězcem "`strGlobal`pro systém k dispozici – to znamená, že všechny paměti přidělené procesem A jsou automaticky uvolněny operačním systémem. Není uvolněna, `CString` protože je volána destruktor; Ještě to nebylo předvoláno. Je uvolněna jednoduše proto, že aplikace, která ji přidělila, opustila scénu. Nyní, pokud `GetGlobalString(sz, sizeof(sz))`B volal , nemusí získat platná data. Některé jiné aplikace mohou použít tuto paměť pro něco jiného.

Je zřejmé, že problém existuje. Knihovna MFC 3.x použila techniku nazvanou místní úložiště (TLS). MFC 3.x by přidělit index TLS, který podle Win32s skutečně funguje jako index místního úložiště procesu, i když není volána, že a pak by odkazovat všechna data na základě tohoto indexu TLS. To je podobné tls index, který byl použit k ukládání místních dat podprocesu na Win32 (viz níže další informace o tomto tématu). To způsobilo, že každá knihovna MFC DLL využívá alespoň dva indexy TLS na proces. Při načtení mnoha ole control knihovny DLL (OCXs), rychle dojdou indexy TLS (k dispozici je pouze 64). Kromě toho mfc musel umístit všechna tato data na jednom místě, v jedné struktuře. Nebylpříliš rozšiřitelný a nebyl ideální, pokud jde o použití indexů TLS.

MFC 4.x řeší to se sadou šablon třídmůžete "obtékat" kolem dat, která by měla být místní zpracování. Například výše uvedený problém může být vyřešen písemně:

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

Knihovna MFC implementuje ve dvou krocích. Nejprve je vrstva nad Win32 __Tls\* __ API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, atd.), které používají pouze dva indexy TLS na proces, bez ohledu na to, kolik DLL máte. Za druhé, šablona `CProcessLocal` je k dispozici pro přístup k těmto datům. To přepíše operátor-> což je to, co umožňuje intuitivní syntaxi vidíte výše. Všechny objekty, které `CProcessLocal` jsou zabaleny, musí být odvozeny od . `CNoTrackObject` `CNoTrackObject`poskytuje alokátor nižší úrovně (**LocalAlloc**/**LocalFree**) a virtuální destruktor tak, aby knihovna MFC může automaticky zničit místní objekty procesu při ukončení procesu. Tyto objekty mohou mít vlastní destruktor, pokud je vyžadováno další vyčištění. Výše uvedený příklad nevyžaduje jeden, protože kompilátor vygeneruje výchozí destruktor zničit vložený `CString` objekt.

Existují i další zajímavé výhody tohoto přístupu. Nejen, že `CProcessLocal` jsou všechny objekty zničeny automaticky, nejsou vytvořeny, dokud nejsou potřeba. `CProcessLocal::operator->`vytvoří instanci přidruženého objektu při prvním volání a nejdříve. Ve výše uvedeném příkladu`strGlobal`to znamená, že řetězec " `SetGlobalString` nebude `GetGlobalString` vytvořen, dokud nebude volán poprvé nebo je volán. V některých případech to může pomoci zkrátit dobu spuštění dll.

## <a name="thread-local-data"></a>Místní data vlákna

Podobně jako zpracování místních dat, místní data vlákna se používá, když data musí být místní pro dané vlákno. To znamená, že potřebujete samostatnou instanci dat pro každé vlákno, které přistupuje k těmto datům. To může být mnohokrát použitna namísto rozsáhlých synchronizačních mechanismů. Pokud data nemusí být sdílena více vlákny, tyto mechanismy mohou být nákladné a zbytečné. Předpokládejme, `CString` že jsme měli objekt (podobně jako vzorek výše). Můžeme to udělat lokální matou tím, že ji zabalíme šablonou: `CThreadLocal`

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Pokud `MakeRandomString` byl volán ze dvou různých vláken, každý by "shuffle" řetězec různými způsoby bez narušení s ostatními. Důvodem je, že `strThread` je ve skutečnosti instance na vlákno namísto pouze jedné globální instance.

Všimněte si, jak odkaz `CString` se používá k zachycení adresy jednou namísto jednou za opakování smyčky. Kód smyčky mohl být `threadData->strThread` napsán`str`s všude ' ' se používá, ale kód by byl mnohem pomalejší v provádění. Je vhodné do mezipaměti odkaz na data, když takové odkazy dojít ve smyčkách.

Šablona `CThreadLocal` třídy používá stejné `CProcessLocal` mechanismy, které dělá a stejné techniky implementace.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
