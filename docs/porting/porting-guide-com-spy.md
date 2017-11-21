---
title: "Průvodce přenosem: COM Spy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e30d0664716df0f4cdf7d394d9c9a5fd7e8c798
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="porting-guide-com-spy"></a>Průvodce přenosem: COM Spy
Toto téma je druhý v řadě články, které ukazuje upgradu starší projekty Visual C++ na nejnovější verzi sady Visual Studio. Ukázkový kód v tomto tématu se poslední kompilovat s Visual Studio 2005.  
  
## <a name="comspy"></a>COMSpy  
 COMSpy je program, který sleduje a zaznamená aktivitu obsluhované komponenty na počítači. Obsluhované komponenty jsou komponenty modelu COM +, které běží v systému a mohou být využívána počítače ve stejné síti. Jste se spravovat pomocí funkce Služba komponent v Ovládacích panelech systému Windows.  
  
### <a name="step-1-converting-the-project-file"></a>Krok 1. Převádění souboru projektu.  
 Soubor projektu převede snadno a vytvoří sestavu migraci. Sestavu, dejte nám vědět, ohledně problémů, které může musíme řešit neobsahuje několik položek. Tady je jeden problém, který je hlášen (Všimněte si, že v tomto tématu se chybové zprávy jsou někdy zkrátit čitelnější, například odebrat úplné cesty):  
  
```Output  
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).  
```  
  
 Jeden z častých problémů v provádění upgrade projektů je, že mají být zkontrolovány může být nutné výstupní soubor Linkeru nastavení v dialogovém okně Vlastnosti projektu. Pro projekty před Visual Studio 2010 výstupní soubor je jedno nastavení, která průvodce automatický převod má potíže s, pokud je nastavená na hodnotu nestandardní. V tomto případě byly nastavené cesty pro výstupní soubory do nestandardní složky XP32_DEBUG. Další informace o této chybě, jsme konzultaci [příspěvku na blogu](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) související s upgrade projektu Visual C++ 2010, která byla upgradu, které se podílejí změnu z vcbuild msbuild významné změny. Podle těchto informací je výchozí hodnota pro nastavení výstupního souboru při vytvoření nového projektu $(OutDir)$(TargetName)$(TargetExt), ale to není nastaven při převodu vzhledem k tomu, že není možné pro převedený projekty k ověření, že je vše Opravte.  Ale můžeme akci, že v umístění pro výstupní soubor a pokud funguje.  Ano, takže se můžeme přesunout. Pokud neexistuje žádný konkrétní důvod pro používání nestandardní výstupní složky, doporučujeme používat standardní umístění. V takovém případě jsme zvolili nechte výstupní umístění, jako nestandardní během procesu upgradu a přenosem; $(Outdir) – přeloží do složky XP32_DEBUG v konfiguraci ladění a složku ReleaseU konfigurace verze.  
  
### <a name="step-2-getting-it-to-build"></a>Krok 2. Načítání sestavení  
 Sestavení přenést projektu, počet chyb a varování dojít.  
  
 I když kvůli této chybě kompilátoru není kompilace ComSpyCtl:  
  
```Output  
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled  
```  
  
 Chyba odkazuje na metodu uložit na třídě IPersistStreamInitImpl v atlcom.  
  
```cpp  
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)  
{  
     T* pT = static_cast<T*>(this);  
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));  
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());  
}  
```  
  
 Problém je, že převodu z starší verze kompilátoru přijata již není platný. Chcete-li v souladu se standardem C++, nějaký kód, který byl dříve povolen již není povoleno. V takovém případě není bezpečné předejte bez const ukazatel na funkci, která očekává ukazatel const.  Řešení je najít deklaraci IPersistStreamInit_Save na CComSpy třídu a přidejte const modifikátor do třetí parametr.  
  
```cpp  
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)  
  
```  
  
 A podobně jako změnu IPersistStreamInit_Load.  
  
```cpp  
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);  
```  
  
 Další chyba přistupuje k registraci.  
  
```Output  
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.  
```  
  
 Tento příkaz registrace po sestavení není již nejsou potřebné. Místo toho jsme jednoduše odeberte příkaz, který vlastní sestavení a zadejte v nastavení Linkeru k registraci výstup.  
  
### <a name="dealing-with-warnings"></a>Práci s upozorněními.  
 Projektu vytvoří následující linkeru upozornění.  
  
```Output  
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification  
```  
  
 / SAFESEH – možnost kompilátoru není v režimu ladění, který je při /EDITANDCONTINUE je užitečné, opravte tady je zakázat/SAFESEH pro ladění konfigurace pouze užitečné. Chcete-li to provést v dialogovém okně Vlastnosti, jsme otevřete dialogové okno Vlastnosti pro projekt, který vytváří tato chyba, a jsme nejdřív nastavit konfiguraci, aby ladění (ve skutečnosti ladění Unicode) a pak v části Upřesnit Linkeru resetovat vlastnost bitové kopie má bezpečné obslužné rutiny výjimek Ne (nebo SAFESEH:NO).  
  
 Kompilátor nám varuje, že PROP_ENTRY_EX je zastaralá. Není bezpečné a PROP_ENTRY_TYPE_EX je doporučené náhrada.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Jsme změňte kód v ccomspy.h odpovídajícím způsobem, přidání typy modelu COM podle potřeby.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)  
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Jsme zasílá na poslední několik upozornění, které jsou také způsobeno více striktní kontroly shody kompilátoru:  
  
```Output  
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'  
```  
  
 Upozornění C4018 pochází z tento kód:  
  
```cpp  
for (i=0;i<lCount;i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 Problém je, že i je deklarován jako Celé_číslo a lCount je deklarován jako dlouho, proto neshoda podepsané nepodepsaných. Je praktické, že lze změnit typ lCount na UINT, protože získá svou hodnotu z IMtsEventInfo::get_Count, která používá typ dlouho a není v uživatelském kódu. Proto přidáme přetypování ke kódu. Přetypování ve stylu jazyka C by to pro číselné přetypování, jako je tato, ale static_cast je doporučené styl.  
  
```cpp  
for (i=0;i<static_cast<UINT>(lCount);i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 Upozornění jsou případy, kde byla proměnná definovaná ve funkci, která má parametr se stejným názvem, což potenciálně složitá kódu. To vyřešili změnou názvy lokální proměnné.  
  
### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění  
 Aplikace jsme testovali nejdřív spuštěním prostřednictvím různých nabídek a příkazů a pak zavření aplikace. Uvedeno pouze problém byl assertion ladění po zavření dolů na aplikaci. V destruktoru se objevil problém pro CWindowImpl, základní třídu objektu CSpyCon hlavní komponenty modelu COM aplikace. V následujícím kódu v atlwin.h došlo k selhání kontrolní výraz.  
  
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
  
 HWnd je standardně nastaven na hodnotu nula ve funkci WindowProc, ale která nebyla docházet proto, že místo výchozího WindowProc, se nazývá vlastní obslužné rutiny pro zprávy systému Windows (WM_SYSCOMMAND), zavře okno. Vlastní obslužná rutina nebyla hWnd nastavení na hodnotu nula. Podívejte se na podobné kódu v MFC je třída CWnd, zobrazuje, když je zničen okno, se nazývá onncdestroy – a v prostředí MFC, dokumentace informuje o tom, které při přepisování CWnd::OnNcDestroy, základní NcDestroy by měla být volána k Ujistěte se, že správné vyčištění dojde k operace, včetně oddělení popisovač okna z okna, nebo jinými slovy, hWnd nastavením na nulu. Tato assert může mít byla spuštěna v původní verzi vzorku a, od ve starší verzi atlwin.h stejný kód kontrolní výraz.  
  
 Pokud chcete testovat funkce aplikace, jsme vytvořili komponentu obsluhovány pomocí šablony projektu knihovny ATL, rozhodli přidat Průvodce projektem ATL COM + podporu. Pokud jste ještě nepracovali s obsluhované komponenty před, není obtížné vytvořit a získat zaregistrovaná a k dispozici v systému nebo síti a použít jiné aplikace. Aplikace modelu COM Spy slouží k monitorování aktivit obsluhované komponenty jako diagnostiky podpory.  
  
 Potom jsme přidat třídu, zvolili objekt knihovny ATL a zadat název objektu jako PSA. Potom v dog.h a dog.cpp jsme přidali implementace.  
  
```cpp  
STDMETHODIMP CDog::Wag(LONG* lDuration)  
{  
    // TODO: Add your implementation code here  
    *lDuration = 100l;  
    return S_OK;  
}  
```  
  
 V dalším kroku jsme vytvořené a registrované ho (budete muset spustit sadu Visual Studio jako správce) a aktivovat ji pomocí aplikace servis součásti v Ovládacích panelech systému Windows. Jsme vytvořili projekt C# Windows Forms, přetažení tlačítko do formuláře z panelu nástrojů a dvakrát, kliknuli na obslužnou rutinu události kliknutí. Jsme přidali následující kód k vytvoření instance komponenty PSA.  
  
```cpp  
private void button1_Click(object sender, EventArgs e)  
{  
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();  
    dog1.Wag();  
}  
```  
  
 To byla spuštěna bez problémů a s COM Spy nahoru a spuštěna a nakonfigurované pro monitorování komponentu PSA velké množství dat zobrazí aktivity.  
  
## <a name="see-also"></a>Viz také  
 [Portování a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Další příklad: Spy ++](../porting/porting-guide-spy-increment.md)   
 [Předchozí příklad: MFC Scribble](../porting/porting-guide-mfc-scribble.md)