---
title: 'Průvodce přenosem: COM Spy'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: f4fece07b9ea4541d8bf21dd81fd659b44f39718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368461"
---
# <a name="porting-guide-com-spy"></a>Průvodce přenosem: COM Spy

Toto téma je druhé z řady článků, které demonstruje proces upgradu starších projektů sady Visual Studio C++ na nejnovější verzi sady Visual Studio. Ukázkový kód v tomto tématu byl naposledy zkompilován pomocí sady Visual Studio 2005.

## <a name="comspy"></a>COMSpy

COMSpy je program, který monitoruje a zaznamenává činnost servisovaných součástí na počítači. Servisované součásti jsou komponenty modelu COM+, které běží v systému a mohou být používány počítači ve stejné síti. Jsou spravovány funkcí Služby komponent v Ovládacích panelech systému Windows.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Převod souboru projektu

Soubor projektu se snadno převede a vytvoří sestavu migrace. V sestavě je několik poznámek, které nám dávají vědět o problémech, které bychom mohli potřebovat řešit. Zde je jeden problém, který je hlášen (všimněte si, že v celém tomto tématu jsou chybové zprávy někdy zkráceny pro čitelnost, například k odstranění úplných cest):

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

Jedním z častých problémů při upgradu projektů je, že nastavení **Propojovací výstupsouboru** v dialogovém okně vlastností projektu může být nutné zkontrolovat. Pro projekty před Visual Studio 2010 OutputFile je jedno nastavení, které průvodce automatickýpřevod má potíže s, pokud je nastavena na nestandardní hodnotu. V tomto případě byly cesty pro výstupní soubory nastaveny na nestandardní složku, XP32_DEBUG. Chcete-li se dozvědět více o této chybě, jsme konzultovali [příspěvek blogu](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) týkající se upgradu projektu Visual Studio 2010, což byl upgrade, který zahrnoval změnu z vcbuild na msbuild, což je významná změna. Podle těchto informací je `$(OutDir)$(TargetName)$(TargetExt)`výchozí hodnota pro nastavení **výstupního souboru** při vytváření nového projektu , ale to není nastaveno během převodu, protože není možné, aby převedené projekty ověřily, že je vše správné. Nicméně, zkusme uvedení, že v pro OutputFile a uvidíme, jestli to funguje.  Ano, takže můžeme jít dál. Pokud neexistuje žádný konkrétní důvod pro použití nestandardní výstupní složky, doporučujeme použít standardní umístění. V tomto případě jsme se rozhodli ponechat výstupní umístění jako nestandardní během procesu přenosu a upgradu; `$(OutDir)` překládá do složky XP32_DEBUG v konfiguraci **ladění** a do složky ReleaseU pro konfiguraci **vydání.**

### <a name="step-2-getting-it-to-build"></a>Krok 2. Jak se stavět

Vytváření portovaného projektu dochází k řadě chyb a upozornění.

`ComSpyCtl`nekompiluje i když kvůli této chybě kompilátoru:

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

Chyba odkazuje na `Save` metodu `IPersistStreamInitImpl` třídy v atlcom.h.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Problém je, že převod, který starší verze kompilátoru přijat a již není platný. Aby bylo možné v souladu se standardem C++, některé kód, který dříve byl povolen již není povoleno. V tomto případě není bezpečné předat ukazatel bez const na funkci, která očekává ukazatel const.  Řešením je najít deklaraci `IPersistStreamInit_Save` na `CComSpy` třídu a přidat modifikátor const do třetího parametru.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

A podobná změna `IPersistStreamInit_Load`.

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

Další chyba se zabývá registrací.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

Už nepotřebujeme tento příkaz k registraci po sestavení. Místo toho jednoduše odebereme příkaz vlastní sestavení a určíme v nastavení **linkeru** pro registraci výstupu.

### <a name="dealing-with-warnings"></a>Nakládání s varováními

Projekt vytvoří následující upozornění propojovacího systému.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

Možnost `/SAFESEH` kompilátoru není užitečná v režimu ladění, což je, `/EDITANDCONTINUE` `/SAFESEH` když je užitečné, takže oprava je zakázáno pouze pro **konfigurace ladění.** Chcete-li to provést v dialogovém okně vlastností, otevřeme dialogové okno vlastností pro projekt, který vytváří tuto chybu, a nejprve nastavíme **konfiguraci** na **ladění** (ve skutečnosti **ladění Unicode**) a potom v části **Linker Advanced** resetuje vlastnost **Image Has Safe Exception Handlers** na **Ne** (`/SAFESEH:NO`).

Kompilátor nás `PROP_ENTRY_EX` varuje, že je zastaralé. Není to bezpečné a doporučená `PROP_ENTRY_TYPE_EX`náhrada je .

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Změníme kód v ccomspy.h odpovídajícím způsobem, přidání maškarní typy podle potřeby.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Dostáváme se k několika posledním upozorněním, která jsou také způsobena přísnějšími kontrolami shody kompilátoru:

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

Upozornění C4018 pochází z tohoto kódu:

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Problém je, `i` že `UINT` je `lCount` deklarován jako a je deklarován jako **dlouho**, proto podepsané/nepodepsané neshody. Bylo by nepohodlné změnit typ `lCount` `UINT`do , protože získá `IMtsEventInfo::get_Count`jeho hodnotu z , který používá typ **long**a není v uživatelském kódu. Takže přidáme obsazení do kódu. Nádech ve stylu C by udělal pro číselné přetypované, jako je tento, ale **static_cast** je doporučený styl.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Tato upozornění jsou případy, kdy byla proměnná deklarována ve funkci, která má parametr se stejným názvem, což vede k potenciálně matoucí kód. Opravili jsme to změnou názvů místních proměnných.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testování a ladění

Testovali jsme aplikaci nejprve spuštěním různých nabídek a příkazů a zavřením aplikace. Jediným známým problémem bylo tvrzení o ladění při zavření aplikace. Problém se objevil v destruktoru pro `CWindowImpl` `CSpyCon` , základní třídy objektu, hlavní komponenty COM aplikace. K selhání kontrolního výrazu došlo v následujícím kódu v souboru atlwin.h.

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

Je `hWnd` obvykle nastavena na `WindowProc` nulu ve funkci, ale to `WindowProc`se nestalo, protože místo výchozího , vlastní obslužná rutina je volána pro zprávu systému Windows (WM_SYSCOMMAND), která zavře okno. Vlastní obslužná `hWnd` rutina nebyla nastavení na nulu. Podívejte se na podobný kód `CWnd` ve třídě knihovny MFC, `OnNcDestroy` ukazuje, že při zničení okna, je volána a v knihovně MFC dokumentace radí, že při přepsání `CWnd::OnNcDestroy`, základna `NcDestroy` by měla být `hWnd` volána, aby se ujistil, že dojde k správné operace vyčištění, včetně oddělení popisovače okna z okna nebo jinými slovy, nastavení na nulu. Toto tvrzení mohlo být spuštěno také v původní verzi ukázky, protože stejný kód kontrolního výrazu byl přítomen ve staré verzi souboru atlwin.h.

Chcete-li otestovat funkce aplikace, jsme **vytvořili serviced component** pomocí šablony projektu KNIHOVNY ATL, rozhodli se přidat podporu modelu COM + v průvodci projektu KNIHOVNY ATL. Pokud jste s obsluhovanými součástmi nepracovali dříve, není těžké ji vytvořit a získat ji zaregistrovanou a dostupnou v systému nebo v síti pro jiné aplikace. Aplikace COM Spy je navržena tak, aby sledovala činnost servisovaných komponent jako diagnostickou pomůcku.

Pak jsme přidali třídu, zvolili objekt KNIHOVNY ATL a zadali název objektu jako `Dog`. Pak v dog.h a dog.cpp jsme přidali implementaci.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Dále jsme jej vytvořili a zaregistrovali (budete muset spustit Visual Studio jako správce) a aktivovali ji pomocí aplikace **Serviced Component** v Ovládacích panelech systému Windows. Vytvořili jsme projekt C# Windows Forms, přetáhli tlačítko do formuláře z panelu nástrojů a poklepali na něj na obslužnou rutinu události kliknutí. Přidali jsme následující kód pro `Dog` vytvoření instance komponenty.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

To běželo bez problémů, a s COM Spy `Dog` a běží a nakonfigurován pro sledování komponenty, spousta dat se objeví ukazuje činnost.

## <a name="see-also"></a>Viz také

[Přenos a upgrade: Příklady a případové studie](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Další příklad: Spy++](../porting/porting-guide-spy-increment.md)<br/>
[Předchozí příklad: Klikačnice knihovny MFC](../porting/porting-guide-mfc-scribble.md)
