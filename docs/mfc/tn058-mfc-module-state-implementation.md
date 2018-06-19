---
title: 'TN058: Implementace stavu modulu MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.implementation
dev_langs:
- C++
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90e407299f67922aa855a51b9983af074cdbd4fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385749"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058: Implementace stavu modulu MFC
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato technická Poznámka popisuje provádění konstrukce "Stavu modulu MFC". Pochopení implementace stavu modulu je důležité pro použití MFC sdílené knihovny DLL z knihovny DLL (nebo serveru v rámci procesu OLE).  
  
 Než si přečtete tuto poznámku, podívejte se na "Správa stavu dat modulů knihovny MFC" v [vytváření nových dokumentů, oken a zobrazení](../mfc/creating-new-documents-windows-and-views.md). Tento článek obsahuje informace o důležitých využití a souhrnné informace o tomto tématu.  
  
## <a name="overview"></a>Přehled  
 Existují tři druhy informace o stavu MFC: stav modulu, stav procesu a stav vlákna. V některých případech mohou být kombinovány tyto typy stavu. Knihovny MFC úchytu mapy jsou například modul místní i místní pro přístup z více vláken. To umožňuje dvě různé moduly do mají různé mapy v každé z jejich vláken.  
  
 Stav procesu a stav vlákna jsou podobné. Tyto datové položky jsou věci, které byly tradičně globální proměnné, ale mají musí být specifické pro daný proces nebo vláken pro podporu správné Win32s nebo pro správné podpora více vláken. Kategorie, které dané datové položky se vejde závisí na daná položka a její požadované sémantiku s ohledem na proces a vlákno hranice.  
  
 Stav modulu je jedinečný, může obsahovat skutečně globální stavu nebo stavu, který je místní proces nebo místní pro přístup z více vláken. Kromě toho je možné vypnout rychle.  
  
## <a name="module-state-switching"></a>Přepnutí stavu modulu  
 Každé vlákno obsahuje ukazatel na stav modulu "aktuální" nebo "aktivní" (logicky ukazatele je součástí místní stavu MFC na vlákno). Tento ukazatel je změnit, pokud podproces provádění předá hranice modulu, například aplikace, volání do prvek OLE nebo knihovny DLL nebo řízení OLE volání zpět do aplikace.  
  
 Aktuální stav modulu je přepnuta voláním **AfxSetModuleState**. Ve většině případů se nikdy práce přímo s rozhraní API. MFC, v řadě případů, zavolá ho pro vás (v WinMain OLE vstupní body, **AfxWndProc**atd.). To se provádí v všechny součásti, které můžete psát pomocí staticky propojení v speciální **WndProc**a speciální `WinMain` (nebo `DllMain`), zná, které modul stavu by měl být aktuální. Zobrazí se tento kód prohlížením DLLMODUL. CPP nebo APPMODUL. CPP v adresáři MFC\SRC.  
  
 Navíc není obvyklé, že chcete nastavit stav modulu a potom není nastavte ji zpět. Ve většině případů chcete "push" vlastní modul stav jako aktuální a potom po dokončení "pop" původní kontextu zpět. K tomu je potřeba makro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) a speciální třída **AFX_MAINTAIN_STATE**.  
  
 `CCmdTarget` má zvláštní funkce pro podporu přepnutí stavu modulu. Konkrétně `CCmdTarget` kořenová třída se používá pro OLE – automatizace a OLE COM – vstupní body. Jako další vstupní bod vystavený v systému, musí tyto vstupní body nastavit stav správný modul. Jak se dané `CCmdTarget` vědět, co stavu "Opravit" modulu by měla být odpověď je "pamatuje" co "aktuální" stav modulu je, když je vytvořený tak, že můžete nastavit aktuální stav modulu, na který "zapamatovaných" názvem hodnotu, pokud je novější. V důsledku toho modul stavu, který daný `CCmdTarget` objekt je přidružený s je stav modulu, který byl aktuální při byl zkonstruován objektu. Trvat jednoduchý příklad načítání serveru INPROC, vytvoření objektu a volání její metody.  
  
1.  Načtení knihovny DLL technologie OLE pomocí **LoadLibrary**.  
  
2. **RawDllMain** jako první. Nastaví stav modulu stavu známé statické modulu pro knihovnu DLL. Z tohoto důvodu **RawDllMain** je staticky propojené na knihovnu DLL.  
  
3.  Konstruktor pro objekt pro vytváření třídy přidružené k naší objektu je volána. `COleObjectFactory` je odvozený od `CCmdTarget` a v důsledku toho pamatuje, ve které modulu stavu, kdy byl vytvořen. To je důležité – při vytváření třídy se zobrazí výzva k vytváření objektů, teď zná co modul stavu, aby aktuální.  
  
4. `DllGetClassObject` je volána k získání objektu pro vytváření tříd. MFC vyhledá seznam objekt pro vytváření tříd přidružený tento modul a vrátí ji.  
  
5. **COleObjectFactory::XClassFactory2::CreateInstance** je volána. Před vytvořením objektu a vrátit, tato funkce nastaví stav modulu stavu modulu, které byly aktuální v kroku 3 (ten, který byl aktuální, kdy `COleObjectFactory` byla vytvořena instance). To se provádí uvnitř [method_prologue –](com-interface-entry-points.md).  
  
6.  Při vytvoření objektu příliš je `CCmdTarget` odvozené a stejným způsobem `COleObjectFactory` zapamatovaných, které stav modulu byl aktivní, takže nemá tento nový objekt. Teď objekt ví, které modul stavu přepnout do vždy, když je volána.  
  
7.  Klient pro volání funkce na objekt OLE COM, obdržel z jeho `CoCreateInstance` volání. Při volání objektu používá `METHOD_PROLOGUE` k přepnutí stavu modulu podobně jako `COleObjectFactory` nepodporuje.  
  
 Jak vidíte, stav modulu z objektu rozšíří do objektu při jejich vytvoření. Je důležité mít stav modulu správně nastavené. Pokud není nastaven, může objektu knihovny DLL nebo COM s aplikace knihovny MFC, který volá, nebo může nelze najít vlastní prostředky nebo může selhat v jiné způsoby miserable špatně komunikovat.  
  
 Všimněte si, že určité druhy knihoven DLL, konkrétně "MFC – rozšiřující" DLL není přepnutí stavu modulu v jejich **RawDllMain** (ve skutečnosti, obvykle i nemají **RawDllMain**). Je to proto, že jsou určeny k chování "jako v případě" byly ve skutečnosti součástí aplikace, která používá je. Jsou velmi mnohem součástí aplikace, která je spuštěna a je svůj záměr upravit globální stav dané aplikace.  
  
 Ovládací prvky OLE a další knihovny DLL se příliš neliší. Není chcete změnit stav volání aplikace; aplikace, která je volá nemusí být i aplikace knihovny MFC a proto je možné změnit bez stavu. To je důvod, aby byla vyvinuta přepnutí stavu modulu.  
  
 Exportované funkce z knihovny DLL, například ten, který spouští dialogové okno v knihovně DLL potřebujete přidejte následující kód do začátku funkce:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState())  
```  
  
 To umožňuje přepnout aktuální stav modulu se stavem vrácená z [afxgetstaticmodulestate –](reference/extension-dll-macros.md#afxgetstaticmodulestate) až do konce aktuálního oboru.  
  
 Problémy s prostředky v knihovnách DLL dojde, pokud `AFX_MODULE_STATE` makro nepoužívá. Ve výchozím nastavení používá MFC popisovač prostředku hlavní aplikace pro načtení šablony prostředků. Tato šablona je ve skutečnosti uložený v knihovně DLL. Hlavní příčinou je, že informace o stavu modulu MFC nebyl byla přepnuta pomocí `AFX_MODULE_STATE` makro. Popisovač prostředku je obnovena ze stavu modulu MFC společnosti. Není přepnutí stavu modulu způsobí, že popisovač nesprávný prostředku, který se má použít.  
  
 `AFX_MODULE_STATE` nemusí být uvést do každé funkce v knihovně DLL. Například `InitInstance` je možné volat v MFC kód aplikace bez `AFX_MODULE_STATE` protože MFC automaticky posune stav modulu před `InitInstance` a pak přepínače zpátky po `InitInstance` vrátí. Totéž platí pro všechny mapování obslužné rutiny zpráv. Regulární knihovny DLL MFC ve skutečnosti mít speciální hlavní okno procedury, která automaticky přepne stav modulu před směrování jakékoli zprávy.  
  
## <a name="process-local-data"></a>Proces místní Data  
 Místní data procesu by neměla mít takové velký dopad kdyby byl pro problém s Win32s DLL modelu. V Win32s všechny knihovny DLL sdílet svá globální data, i když načíst více aplikacemi. Toto je příliš neliší od "Skutečná" Win32 DLL datový model, kde každou knihovnu DLL, získá samostatnou kopii jeho datového prostoru v jednotlivých procesů, který připojí na knihovnu DLL. Přidat do složitosti, data přidělené v haldě v knihovně DLL Win32s je ve skutečnosti proces specifický (alespoň pokud vlastnictví přejde). Vezměte v úvahu následující data a kódu:  
  
```  
static CString strGlobal; // at file scope  
 
__declspec(dllexport)   
void SetGlobalString(LPCTSTR lpsz)  
{  
    strGlobal = lpsz;  
}  
 
__declspec(dllexport)  
void GetGlobalString(LPCTSTR lpsz,
    size_t cb)  
{  
    StringCbCopy(lpsz,
    cb,
    strGlobal);

}  
```  
  
 Zvažte, co se stane, pokud ve výše uvedeném kódu v nachází v knihovně DLL a že načte se knihovna DLL dva procesy A a B (může ve skutečnosti je dvě instance stejné aplikace). Volání `SetGlobalString("Hello from A")`. V důsledku toho se přidělí paměť pro `CString` data v rámci procesu A. Mějte na paměti, že `CString` samostatně je globální a je viditelná pro oba A a B. Nyní B volá `GetGlobalString(sz, sizeof(sz))`. B bude moci zobrazit data, která A nastavit. To je proto Win32s nabízí žádná ochrana mezi procesy, jako jsou Win32 nepodporuje. To je první problém; v mnoha případech není žádoucí, aby aplikací mít vliv na globální data, která se považuje za vlastnit jinou aplikaci.  
  
 Existují také další problémy. Řekněme, že teď ukončí. Když A ukončí, množství paměti používané '`strGlobal`' řetězec je k dispozici pro systém – to znamená, že všechny paměti přidělené procesu A uvolní automaticky podle operačního systému. Není vydání, protože `CString` volá destruktor; nebyla ještě volána. Je jednoduše uvolněno vzhledem k tomu, že aplikace, které ho přidělilo opustil scény. Teď Pokud volána B `GetGlobalString(sz, sizeof(sz))`, ale nemusí získat platná data. Jiná aplikace může použít tuto paměť pro něco jiného.  
  
 Jasně problém existuje. MFC 3.x použít techniku zvanou úložiště thread-local (TLS). MFC 3.x by přidělit TLS index, který v rámci Win32s skutečně funguje jako index proces místní úložiště, i když není volán, který a by pak odkazovat všechna data podle tohoto indexu TLS. Toto je podobný TLS index, který byl použit k ukládání dat místním na Win32 (Další informace o tomto předmětu viz níže). Příčinou každých MFC DLL využívat aspoň dva indexy TLS podle procesu. Pokud jste účet pro načítání mnoho OLE řízení knihoven DLL (soubory OCX), je rychle spustit mimo indexy TLS (existuje pouze 64). Kromě toho MFC museli umístit tato data na jednom místě, do jednoho struktury. Ho nebyla velmi rozšiřitelný a nebyl ideální s ohledem na jeho použití protokolu TLS indexů.  
  
 MFC 4.x adresy to sadu šablony třídy můžete "zabalit" kolem data, která by měla být místní proces. Například může problém zmíněné opravit napsáním:  
  
```  
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
  
 MFC implementuje to ve dvou krocích. První je vrstva nad Win32 **Tls\***  rozhraní API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**atd) který použijte pouze dva indexy TLS podle procesu, bez ohledu na to, kolik knihovny DLL, které máte. Druhý, `CProcessLocal` šablony je zadán pro přístup k těmto datům. Přepíše operátor ->, který je co umožňuje intuitivní syntaxe zobrazeny výše. Všechny objekty, které nejsou zabalené službou `CProcessLocal` musí být odvozen od `CNoTrackObject`. `CNoTrackObject` poskytuje allocator nižší úrovně (**LocalAlloc**/**LocalFree**) a virtuální destruktor tak, aby MFC můžete automaticky destroy místní objekty procesu, při ukončení procesu. Tyto objekty může mít vlastní destruktor, pokud je potřeba další čištění. Výše uvedeném příkladu nevyžaduje, 1, protože výchozí destruktor zrušení vložený vygeneruje kompilátor `CString` objektu.  
  
 Existují další zajímavé výhody tohoto přístupu. Ne jenom jsou všechny `CProcessLocal` objekty zničen automaticky, že nejsou sestavený, dokud není potřeba. `CProcessLocal::operator->` vytvoří instanci přidruženého objektu při prvním volání a dřív. V příkladu nahoře, která znamená, že '`strGlobal`' řetězec nebude zkonstruovat až poprvé **SetGlobalString** nebo **GetGlobalString** je volána. V některých případech to může pomoct snížit čas spuštění knihovny DLL.  
  
## <a name="thread-local-data"></a>Místní Data přístup z více vláken  
 Podobně jako při zpracování místní data, přístup z více vláken místní data se používají při data musí být místní pro dané vlákno. To znamená potřebujete samostatnou instanci data pro každý podproces, který přistupuje k těmto datům. Kolikrát slouží místo mechanismy rozsáhlé synchronizace. Pokud data nemusí být sdílen více vláken, může být mechanismů nákladné a zbytečné. Předpokládejme, že jsme měli `CString` objektu (podobně jako ukázka výše). Jsme může být přístup z více vláken místní podle její zabalení `CThreadLocal` šablony:  
  
```  
struct CMyThreadData : public CNoTrackObject  
{  
    CString strThread;  
};  
CThreadLocal<CMyThreadData> threadData;  
 
void MakeRandomString()  
{ *// a kind of card shuffle (not a great one)  
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
  
 Pokud `MakeRandomString` byla volána ze dvou různých vláknech, každý by "náhodně" řetězec různými způsoby bez ovlivnění dalších. Důvodem je, že je ve skutečnosti a `strThread` instance pro každý vláknem a nikoli jen jedna globální instance.  
  
 Všimněte si, jak odkaz se používá k zachycení `CString` adres jednou místo jednou za iteraci smyčky. Kód smyčky by byl zapsán s `threadData->strThread` everywhere '`str`' se používá, ale kód by výrazně zpomalit při provádění. Je nejvhodnější mezipaměti odkaz na data, když se tyto odkazy, ke kterým došlo v smyčky.  
  
 `CThreadLocal` Třída šablona používá stejné mechanismy, `CProcessLocal` nepodporuje a se stejné techniky implementace.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

