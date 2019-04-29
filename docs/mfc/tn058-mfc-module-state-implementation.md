---
title: 'TN058: Implementace stavu modulu MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.implementation
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: db34f528e70a7dcc437836684656b3ce8a4078fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399593"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementace stavu modulu MFC

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato technická Poznámka Popisuje implementaci konstruktorů "Stavu modulu MFC". Znalost implementace stavu modulu je velmi důležité pro použití prostředí MFC sdílených knihoven DLL z knihovny DLL (nebo OLE v procesový server).

Před čtením této poznámky o "Správa the stav dat modulů knihovny MFC" v [vytváření nových dokumentů, Windows a zobrazení](../mfc/creating-new-documents-windows-and-views.md). Tento článek obsahuje důležité informace a přehled informací o této skutečnosti.

## <a name="overview"></a>Přehled

Existují tři druhy informací o stavu knihovny MFC: Stav modulu, stav procesu a stav vlákna. V některých případech mohou být kombinovány tyto typy stavu. Mapování zpracování MFC jsou například místní modul a místního vlákna. To umožňuje dvou různých modulech mít různých map v každé z jejich vlákna.

Stav procesu a stav vlákna jsou podobné. Tyto datové položky jsou věci, které tradičně globální proměnné, ale mají musí být specifické pro daný proces nebo vlákno pro podporu správné Win32s nebo podpora multithreadingu ve správné. Která kategorie dané datové položky vejde závisí na danou položku a její požadované sémantika s ohledem na hranice procesu a vlákně.

Stav modulu je jedinečný v tom, že může obsahovat skutečně globální stav nebo stav, který je místní proces nebo vlákno místní. Kromě toho je možné vypnout rychle.

## <a name="module-state-switching"></a>Přepnutí stavu modulu

Každé vlákno obsahuje ukazatel na stav "aktuální" nebo "aktivní" modulu (logicky ukazatel je součástí stav místního vlákna MFC). This – ukazatel se změní, pokud vlákno provádění předává modulu hranice, například aplikace volání do OLE ovládací prvek nebo knihovny DLL nebo ovládacího prvku OLE zpětné volání do aplikace.

Přepne aktuální stav modulu voláním `AfxSetModuleState`. Ve většině případů které se postará nikdy přímo s rozhraním API. Knihovny MFC, v mnoha případech bude volat ho za vás (na WinMain, OLE vstupní body, `AfxWndProc`atd.). To se provádí v libovolné součásti zápisu pomocí statického propojení v speciální `WndProc`a speciální `WinMain` (nebo `DllMain`), které ví, které modul stav by měl být aktuální. Zobrazí se tento kód zobrazením DLLMODUL. CPP nebo APPMODUL. CPP v adresáři MFC\SRC.

Je vzácné, že chcete nastavit stav modulu a potom Nenastaveno ho zpátky. Ve většině případů chcete "push" vlastní modul stavu jako aktuální a pak, jakmile budete hotovi, "vyvolat přes pop" původního kontextu. Uděláte to pomocí makra [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) a speciální třídy `AFX_MAINTAIN_STATE`.

`CCmdTarget` má speciální funkce pro podporu modulu přepnutí stavu. Konkrétně se `CCmdTarget` je kořenová třída používá k automatizaci OLE a OLE COM – vstupní body. Všechny ostatní vstupní bod, jako jsou zveřejněné v systému, musí tyto vstupní body nastavit stav správný modul. Jak se dané `CCmdTarget` vědět, co "Opravit" modul stav by měl být odpověď je, že "pamatuje" co je "aktuální" stavu modulu při jejím vytváření, tak, že můžete nastavit aktuální stav modulu, který "uloží" hodnotu, pokud je novější volá. V důsledku toho modul uvádějí, že daný `CCmdTarget` objekt je přidružený se stav modulu, který byl aktuální, když byl objekt vytvořen. Provést jednoduchý příklad načítání serveru INPROC, vytvoření objektu a volat jeho metody.

1. Načtení knihovny DLL technologie OLE pomocí `LoadLibrary`.

2. `RawDllMain` jako první. Nastaví stav modulu stavu známé statické modulu pro knihovnu DLL. Z tohoto důvodu `RawDllMain` je staticky propojena s knihovnou DLL.

1. Konstruktor pro objekt pro vytváření tříd přidružený k naší objektu je volána. `COleObjectFactory` je odvozen z `CCmdTarget` a v důsledku toho zapamatuje, v jakém stavu modulu byla vytvořena instance. To je důležité – když objekt pro vytváření tříd se zobrazí výzva k vytvoření objektů, nyní ví jednotlivých stavech modulu na nastavit jako aktuální.

4. `DllGetClassObject` je volána k získání objektu pro vytváření tříd. Knihovna MFC vyhledá v seznamu továren třídy přidružené k tento modul a vrátí jej.

5. `COleObjectFactory::XClassFactory2::CreateInstance` je volána. Před vytvořením objektu a jeho vrácením, tato funkce nastaví stav modulu do stavu modulu, který byl aktuální v kroku 3 (ten, který byl aktuální, kdy `COleObjectFactory` byla vytvořena instance). To se provádí uvnitř [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Při vytvoření objektu je příliš je `CCmdTarget` odvozená díla a stejným způsobem `COleObjectFactory` uloží, které stav modulu byl aktivní, proto nemá tento nový objekt. Nyní objektu ví, které modul stavu přepnout na vždy, když je volána.

1. Klient volá funkci na objektu OLE COM přijal z jeho `CoCreateInstance` volání. Při volání objektu používá `METHOD_PROLOGUE` k přepnutí stavu modulu stejně jako `COleObjectFactory` nepodporuje.

Jak je vidět, stavu modulu je rozšířena z objektu na objekt při jejich vytvoření. Je důležité mít stav modulu odpovídajícím způsobem nastavit. Pokud není nastavená, může váš objekt modelu COM nebo knihovny DLL špatně interakci s aplikace knihovny MFC, která je volání, nebo možná nebudete moct najít vlastní prostředky nebo jiným způsobem občas může selhat.

Všimněte si, že některé druhy knihoven DLL, konkrétně "MFC – rozšiřující" DLL nepřepínejte stav modulu v jejich `RawDllMain` (ve skutečnosti, že obvykle ještě nemají `RawDllMain`). Je to proto, že jsou určeny k chování "jako kdyby" byly ve skutečnosti k dispozici v aplikaci, která je používá. Jsou velmi dobře součástí aplikace, na kterém běží a je svůj záměr měnit globální stav vaší aplikace.

Ovládací prvky OLE a další knihovny DLL se velmi liší. Chcete-li změnit stav volání aplikace; nechtějí aplikace, která je volá ještě nemusí být aplikace knihovny MFC a tak můžou existovat žádný stav změnit. To je důvod, že byla vyvinuta přepnutí stavu modulu.

Exportovaných funkcí z knihovny DLL, jako je ten, který spustí dialogové okno v knihovně DLL budete muset přidat následující kód na začátek funkce:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

To Zamění aktuální stav modulu se stavem vrácená [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate) až do konce v aktuálním oboru.

Problémy s prostředky v knihovnách DLL dojde, pokud se nepoužívá afx_module_state – makro. Ve výchozím nastavení knihovna MFC používá k načtení šablony prostředků popisovač prostředku hlavní aplikace. Tato šablona je ve skutečnosti uložené v knihovně DLL. Hlavní příčinou je, že informace o stavu modulů knihovny MFC nebyl bylo změněno pomocí afx_module_state – makro. Popisovač prostředku je obnovena ze stavu modulu MFC. Není přepnutí stavu modulu způsobí, že popisovač Chybný prostředek má být použit.

Afx_module_state – není potřeba umístit do každé funkce v knihovně DLL. Například `InitInstance` je možné vyvolat v kódu knihovny MFC v aplikaci bez afx_module_state – protože MFC automaticky nastaven stav modulu před `InitInstance` a pak přepínače ji zpět po `InitInstance` vrátí. Totéž platí pro všechny mapování obslužné rutiny zpráv. Regulární knihovny DLL MFC ve skutečnosti mít speciální hlavní okno procedury, která automaticky přepne před směrováním jakákoliv zpráva o stavu modulu.

## <a name="process-local-data"></a>Místní zpracování dat

Místní zpracování dat by se takové hodně záleží, kdyby byly potíže Win32s DLL modelu. V Win32s všechny knihovny DLL sdílet svá globální data, i v případě, že se načetl více aplikací. Tím se velmi liší od "real" Win32 DLL datový model, kde každou knihovnu DLL načte samostatnou kopii místo jeho data v jednotlivých procesů, který se připojuje k souboru DLL. Přidat složitost, data přidělený k haldě v knihovně DLL Win32s je ve skutečnosti konkrétní proces (minimální míře přejde vlastnictví). Vezměte v úvahu následující data a kód:

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

Zvažte, co se stane, pokud ve výše uvedeném kódu je v umístěný v knihovně DLL a že se načte knihovna DLL dva procesy A a B (můžete je ve skutečnosti je dvě instance stejné aplikace). Volání `SetGlobalString("Hello from A")`. V důsledku toho je paměť přidělena pro `CString` dat v rámci procesu a mějte na paměti, že `CString` samotného je globální a je viditelný pro obě A a B. Teď volá B `GetGlobalString(sz, sizeof(sz))`. B, budete moct zobrazit data A nastavení. Je to proto Win32s nabízí žádná ochrana mezi procesy jako Win32. Který je prvním problémem; v mnoha případech není žádoucí, aby jednu aplikaci vliv globální data, která se považuje za vlastněné jinou aplikaci.

Existují i další problémy. Řekněme, že se teď ukončí. Když A ukončí, paměť používanou "`strGlobal`" řetězec je k dispozici pro systém – to znamená veškerou paměť přidělenou procesu A uvolní automaticky podle operačního systému. Není uvolněn, protože `CString` destruktoru je volána, nebyl dosud byla volána. To je uvolněna pouze vzhledem k tomu, že aplikace, které ho přidělilo opustil scény. Když teď volá B `GetGlobalString(sz, sizeof(sz))`, ale nemůže získat platná data. Některé aplikace mohou použít tuto paměť na něco jiného.

Jasně existuje problém. MFC 3.x používá techniky označované jako úložiště thread local (TLS). MFC 3.x by přidělit TLS index, že je v části Win32s skutečně funguje jako index procesu místní úložiště, i když to není volána a pak bude odkazovat na všechna data podle indexu TLS. Toto je podobný TLS index, který byl použit k ukládání místních dat v systému Win32 (Další informace o tomto tématu najdete níže). Důvodem každou knihovnu DLL MFC využívat aspoň dva TLS indexů procesu. Pokud jste účet pro načítání mnoho OLE ovládacího prvku knihovny DLL (soubory OCX), rychle vyčerpáte indexy TLS (existuje pouze 64 k dispozici). Kromě toho MFC museli umístit všechna tato data na jednom místě, do jednoho struktury. Nebyla velmi rozšiřitelný a není ideální s ohledem na jeho použití protokolu TLS indexů.

MFC 4.x řeší to sadu šablony třídy lze "zabalením" kolem data, která by měla být místní proces. Například výše uvedených problém by se daly odstranit zápisu:

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

Knihovna MFC implementuje to ve dvou krocích. První je vrstvu nad Win32 __Tls\*__  rozhraní API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**atd) který použijte pouze dva TLS indexů na proces, bez ohledu na to, kolik knihovny DLL, je nutné. Druhý, `CProcessLocal` šablony je k dispozici pro přístup k těmto datům. Přepíše operator ->, který je co umožňuje intuitivní syntaxi najdete výše. Všechny objekty, které jsou zabaleny ve `CProcessLocal` musí být odvozen od `CNoTrackObject`. `CNoTrackObject` poskytuje nižší úrovně alokátoru (**LocalAlloc**/**LocalFree**) a virtuální destruktor tak, aby knihovny MFC lze automaticky zničit objekty místní proces, při ukončení procesu. Tyto objekty může mít vlastní destruktor, pokud je potřeba další čištění. Výše uvedený příklad nevyžaduje, aby jeden, protože kompilátor bude generovat výchozí destruktor ke zničení vložený `CString` objektu.

Existují další zajímavé výhody tohoto přístupu. Nejen všechny jsou `CProcessLocal` objekty zničeny, automaticky se nejsou vytvořen, dokud nejsou potřeba. `CProcessLocal::operator->` vytvoří instanci přidruženého objektu okamžiku, kdy je volána a dřív. V předchozím příkladu to znamená, že "`strGlobal`" řetězec nebude vytvořena až do první `SetGlobalString` nebo `GetGlobalString` je volána. V některých případech to může pomoct snížit dobu spuštění knihovny DLL.

## <a name="thread-local-data"></a>Místní Data vlákna

Podobně jako u zpracovat místní data se dat thread local se používá při data musí být místní pro dané vlákno. To znamená, že potřebujete samostatnou instanci data pro každý podproces, který přistupuje k těmto datům. Tímto v mnoha případech lze namísto mechanismy rozsáhlé synchronizace. Pokud se data nemusí být sdíleny více vlákny, tyto mechanismy může být nákladná a zbytečné. Předpokládejme, že jsme měli `CString` objekt (podobně jako příkladu výše). Může být ještě vlákna místní obalením ji `CThreadLocal` šablony:

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

Pokud `MakeRandomString` byla volána z dvou různých vláken, každý by "shuffle" řetězec různými způsoby aniž by zasahovala do druhé. Důvodem je, že je ve skutečnosti `strThread` instance pro každý vláknem a nikoli pouze jedna globální instance.

Všimněte si, jak se používá odkaz k zachycení `CString` adresy jednou místo jednou za iteraci smyčky. Kód smyčky by mohl být napsán s `threadData->strThread` everywhere "`str`' se používá, ale bude pomalejší při provádění kódu. Je nejlepší pro ukládání do mezipaměti odkaz na data, dojde-li tyto odkazy jsou ve smyčkách.

`CThreadLocal` Šablony třídy používá stejné mechanismy, které `CProcessLocal` nepodporuje a stejné techniky implementace.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
