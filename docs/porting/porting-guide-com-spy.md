---
title: 'Průvodce přenosem: COM Spy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8a4278d89727f47e85d20809060fc8cef421998
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427209"
---
# <a name="porting-guide-com-spy"></a>Průvodce přenosem: COM Spy

Toto téma je druhý v sérii článků, který znázorňuje proces upgradu na nejnovější verzi sady Visual Studio starší projekty Visual C++. Pomocí sady Visual Studio 2005 poslední kompilaci kódu příklad v tomto tématu.  
  
## <a name="comspy"></a>COMSpy  
 
COMSpy je program, který sleduje a protokoluje aktivitu obsluhované komponenty v počítači. Obsluhované komponenty jsou komponenty COM +, které v počítači a můžou používat počítače ve stejné síti. Jsou spravovaná přes funkci Služba komponent v Ovládacích panelech Windows.  
  
### <a name="step-1-converting-the-project-file"></a>Krok 1. Převádí se projektový soubor.  
Soubor projektu převede snadno a vytváří sestavy migrace. Existuje několik položek v sestavě, která nás informuje o problémech, které se musíme zabývat. Tady je jeden problém, který se použije v hlášení (Všimněte si, že v tomto tématu se chybové zprávy jsou někdy zkrátila pro lepší čitelnost, třeba když chcete odebrat úplné cesty):  
  
```Output  
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).  
```  
  
Jednou z častých problémech v provádění upgrade projektů, která je **Linkeru OutputFile** nastavení v dialogovém okně Vlastnosti projektu může být nutné zkontrolovat. Pro projekty před Visual Studio 2010 OutputFile je jedním z nastavení, která v Průvodci převodem automatické má potíže s tím, pokud je nastavena na hodnotu nestandardní. Cesty pro výstupní soubory v tomto případě byla nastavena na složku nestandardní XP32_DEBUG. Najít další informace o této chybě, jsme konzultaci [blogový příspěvek](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) související s upgrade projektu Visual C++ 2010, která byla upgradu, které se podílejí změna vcbuild msbuild, významnou změnu. Podle těchto informací se výchozí hodnota pro **výstupní soubor** nastavení při vytváření nového projektu je `$(OutDir)$(TargetName)$(TargetExt)`, ale to není nastaven při převodu, protože není možné u převedený projektů a ověřte, zda všechno, co je správná. Ale můžeme zkuste uvedení, že pro výstupní soubor a pokud to funguje.  Ano, takže se můžeme přesunout. Pokud neexistuje žádný konkrétní důvod pro používání nestandardní výstupní složky, doporučujeme použít standardní umístění. V tomto případě jsme zvolili ponechat umístění výstupu jako nestandardní během procesu přenos a upgrade. `$(OutDir)` přeloží do složky XP32_DEBUG v **ladění** konfigurace a ReleaseU složku **vydání** konfigurace.  
  
### <a name="step-2-getting-it-to-build"></a>Krok 2. Načítání sestavení  
Sestavení přenesená projektu, dojde k počtu chyb a upozornění.  
  
`ComSpyCtl` i když kvůli této chybě kompilátoru nebude kompilace:  
  
```Output  
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled  
```  
  
Chyba odkazy `Save` metodu `IPersistStreamInitImpl` třídy v atlcom.  
  
```cpp  
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)  
{  
     T* pT = static_cast<T*>(this);  
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));  
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());  
}  
```  
  
Problém je, že převod, který starší verzi kompilátoru přijetí již není platný. Aby bylo možné v souladu se standardem jazyka C++, kód, který byl dřív povolen již není povolena. V takovém případě není bezpečné k předání nekonstantního ukazatele na funkci, která očekává ukazatel const.  Toto řešení je k vyhledání deklarace `IPersistStreamInit_Save` na `CComSpy` tříd a přidejte const modifikátor třetí parametr.  
  
```cpp  
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)   
```  
  
A podobné změny `IPersistStreamInit_Load`.  
  
```cpp  
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);  
```  
  
Další chyba se zabývá registrace.  
  
```Output  
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.  
```  
  
Tento příkaz pro registraci. po sestavení už nepotřebujeme. Místo toho jsme jednoduše odeberte příkaz, který vlastní sestavení a zadejte v **Linkeru** nastavení registrovat výstup.  
  
### <a name="dealing-with-warnings"></a>Práce s upozorněními.  
Projekt vytvoří následující linker upozornění.  
  
```Output  
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification  
```  
  
`/SAFESEH` – Možnost kompilátoru není užitečný v režimu ladění, což je při `/EDITANDCONTINUE` je užitečné, protože zde opravy je zakázat `/SAFESEH` pro **ladění** pouze konfigurace. K tomu v dialogovém okně Vlastnosti nám otevřít dialogové okno vlastností pro projekt, který vytváří tato chyba, a doporučujeme nejdříve nastavit **konfigurace** k **ladění** (ve skutečnosti **ladění Unicode**) a pak v **Linker Advanced** části, resetovat **bitové kopie má bezpečné obslužné rutiny výjimek** vlastnost **č** (`/SAFESEH:NO`).  
  
Kompilátor vás upozorní, USA, který `PROP_ENTRY_EX` je zastaralý. Není bezpečné a je doporučenou náhrada `PROP_ENTRY_TYPE_EX`.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
Jsme kód v ccomspy.h odpovídajícím způsobem měnit, přidávání typů modelu COM podle potřeby.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)  
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
Opakují na poslední několik upozornění, která jsou také způsobeno přísnější kontroly shody kompilátoru:  
  
```Output  
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'  
```  
  
Upozornění C4018 pochází z tento kód:  
  
```cpp  
for (i=0;i<lCount;i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
Problém je, že `i` je deklarován jako `UINT` a `lCount` je deklarován jako **dlouhé**, proto neshoda podepsané nebo nepodepsané. Je vhodná, chcete-li změnit typ `lCount` k `UINT`, protože získá svou hodnotu z `IMtsEventInfo::get_Count`, který používá typ **dlouhé**a není v uživatelském kódu. Proto jsme do kódu přidat přetypování. Přetypování C-style byste to udělali pro číselné přetypování takovou situaci, ale **static_cast** je doporučené styl.  
  
```cpp  
for (i=0;i<static_cast<UINT>(lCount);i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
Upozornění jsou případy, kde byla proměnná deklarovaná ve funkci, která má parametr se stejným názvem, což vede k potenciálně matoucí kódu. Jsme odstranili, změníte názvy místních proměnných.  
  
### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění  
Otestovali jsme aplikaci nejprve spuštěním prostřednictvím různých nabídek a příkazů, a pak ukončit aplikaci. Pouze problémy, které jste si poznamenali byly kontrolní výraz ladění při ukončete aplikaci. Tento problém objevil v destruktoru pro `CWindowImpl`, základní třídu `CSpyCon` objektu, komponenty modelu COM hlavní aplikace. V následujícím kódu v atlwin.h došlo k selhání kontrolního výrazu.  
  
```cpp  
virtual ~CWindowImplRoot()  
{  
     #ifdef _DEBUG  
     if(m_hWnd != NULL)// should be cleared in WindowProc  
     {  
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));  
          ATLASSERT(FALSE);  
     }  
     #endif //_DEBUG  
}  
```  
  
`hWnd` Je obvykle nastavena na nulu `WindowProc` funkce, ale neměli dojít, protože místo výchozího `WindowProc`, se nazývá vlastní obslužné rutiny zprávy Windows (WM_SYSCOMMAND), zavře okno. Nebyl nastavení vlastní obslužné rutiny `hWnd` na nulu. Podívejte se na podobný kód v knihovně MFC `CWnd` třídy, ukazuje, že při zničení okno `OnNcDestroy` je názvem a v knihovně MFC, dokumentaci, která doporučí při přepisování `CWnd::OnNcDestroy`, základní `NcDestroy` by měla být volána, abyste měli jistotu, že vpravo dojde k vyčištění operace, včetně oddělení popisovač okna z okna, nebo jinými slovy, nastavení `hWnd` na nulu. Tento kontrolní výraz může být byla aktivována v původní verzi ukázky, protože byla k dispozici ve starší verzi atlwin.h stejný kód kontrolní výraz.  
  
Pokud chcete otestovat funkčnost aplikace, jsme vytvořili **obsluhované komponenty** pomocí šablony projektu ATL, se rozhodli přidat Průvodce projektem ATL COM + podporu. Pokud jste ještě nepracovali s obsluhované komponenty před, není složité ho vytvořit a získat registrované a k dispozici v systému nebo v síti pro jiné aplikace, které používají. Aplikace modelu COM Spy je určené k monitorování aktivit obsluhované komponenty jako diagnostickou pomůcku.  
  
Potom jsme přidali třídy, zvolili objekt knihovny ATL a zadat název objektu jako `Dog`. Potom v dog.h a dog.cpp jsme přidali implementace.  
  
```cpp  
STDMETHODIMP CDog::Wag(LONG* lDuration)  
{  
    // TODO: Add your implementation code here  
    *lDuration = 100l;  
    return S_OK;  
}  
```  
  
Dále jsme vytvořené a registrované ho (bude nutné spustit sadu Visual Studio jako správce) a aktivovat ji pomocí **obsluhované komponenty** aplikace v Ovládacích panelech Windows. Jsme vytvořili projekt C# Windows Forms, přetáhnout tlačítka do formuláře z panelu nástrojů a který dvakrát kliknuli na obslužnou rutinu události click. Přidali jsme následující kód k vytvoření instance `Dog` komponenty.  
  
```cpp  
private void button1_Click(object sender, EventArgs e)  
{  
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();  
    dog1.Wag();  
}  
```  
  
To běžel bez problémů a s COM Spy zprovozněný a konfiguruje pro monitorování `Dog` součástí, zobrazí se velké množství dat znázorňující aktivity.  
  
## <a name="see-also"></a>Viz také  

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Následující příklad: Spy ++](../porting/porting-guide-spy-increment.md)<br/>
[Předchozí příklad: MFC Scribble](../porting/porting-guide-mfc-scribble.md)