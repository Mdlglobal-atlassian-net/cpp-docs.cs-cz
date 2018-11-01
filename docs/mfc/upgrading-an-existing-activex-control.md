---
title: Upgradování existujícího ovládacího prvku ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
ms.openlocfilehash: 18641c6e25aaccd6b5d0bcbbddbf8fc73b2a3c52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525798"
---
# <a name="upgrading-an-existing-activex-control"></a>Upgradování existujícího ovládacího prvku ActiveX

Ovládací prvky ActiveX existující (dříve ovládací prvky OLE) je možné na Internetu bez úprav. Však můžete chtít upravit ovládací prvky pro zlepšení výkonu.

> [!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Při použití ovládacího prvku na webové stránce, některé další aspekty. Soubor .ocx a všechny podpůrné soubory musí být na cílovém počítači nebo stáhnout přes Internet. Díky tomu velikost kódu a stažení čas, což je důležité. Soubory ke stažení se dá zabalit do souboru .cab podepsaný držitelem. Můžete označit jako bezpečné pro skriptování a jako bezpečné pro inicializaci ovládacího prvku.

Tento článek popisuje v následujících tématech:

- [Balení kódu pro stahování](#_core_packaging_code_for_downloading)

- [Označení ovládací prvek bezpečný pro skriptování a inicializaci](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problémy s licencí](#_core_licensing_issues)

- [Podepisování kódu](#_core_signing_code)

- [Správa palety](#_core_managing_the_palette)

- [Úrovně zabezpečení prohlížeče Internet Explorer a chování ovládacího prvku](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Můžete také přidat optimalizace, jak je popsáno v [ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md). Monikery je možné stáhnout vlastnosti a velké objekty BLOB asynchronně, jak je popsáno v [ovládací prvky Activexna Internetu](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a> Balení kódu pro stahování

Další informace o této skutečnosti najdete v tématu [ovládací prvky ActiveX balení](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>Značka základu kódu

Ovládací prvky ActiveX jsou vloženy do webových stránek pomocí `<OBJECT>` značky. `CODEBASE` Parametr `<OBJECT>` značka Určuje umístění, ze kterých mají být staženy ovládacího prvku. `CODEBASE` může odkazovat na mnoha různých typech souborů úspěšně.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Použijte značku základu kódu se souborem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Toto řešení stáhne jenom soubory .ocx ovládacího prvku a vyžaduje všechny podpůrné knihovny DLL již být nainstalovaný na klientském počítači. To bude fungovat pro Internet Explorer a ActiveX knihovny MFC ovládací prvky vytvořené v jazyce Visual C++, protože aplikace Internet Explorer se dodává s podpůrné knihovny DLL pro ovládací prvky jazyka Visual C++. Pokud jiný prohlížeč Internetu, který je podporuje ovládací prvek ActiveX se používá k zobrazení tohoto ovládacího prvku, toto řešení nebude fungovat.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Značka základu kódu pomocí souboru INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Soubor s příponou INF bude řídit instalaci .ocx a jeho podpůrné soubory. Tato metoda se nedoporučuje, protože není možné k podepsání souboru INF (viz [podepisování kódu](#_core_signing_code) pro ukazatele na podepisování kódu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Použijte značku základu kódu se souborem CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

CAB soubory jsou doporučeným způsobem, jak balíček – ovládací prvky ActiveX, které používají knihovnu MFC. Balení ovládací prvek ActiveX knihovny MFC v souboru CAB umožňuje soubor s příponou INF mají být zahrnuty do ovládacího prvku instalace ovládacího prvku ActiveX a všechny závislé knihovny DLL (jako je například knihovny MFC DLL). Použití souboru CAB automaticky komprimuje kódu pro rychlejší stahování. Pokud používáte soubor .cab pro součástí ke stažení, je rychlejší k podepsání souboru CAB celý než jednotlivých komponent.

### <a name="creating-cab-files"></a>Vytváření souborů CAB

Nástroje pro vytváření souboru CAB soubory jsou teď součástí [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Soubor CAB odkazuje `CODEBASE` by měl obsahovat soubor .ocx ovládacího prvku ActiveX a soubor s příponou INF řídit její instalaci. Vytvořte soubor CAB tak, že zadáte název ovládacího prvku souboru a soubor s příponou INF. Nezahrnují závislé knihovny DLL, které mohou již existovat v systému v tomto souboru CAB. Například knihovny DLL MFC jsou zabalené v samostatném souboru CAB a řídící soubor INF.

Podrobnosti o tom, jak vytvořit soubor CAB najdete v tématu [vytváření souboru CAB](/windows/desktop/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Soubor INF

Následující příklad, spindial.inf, seznamy podpůrné soubory a informace o verzi potřebné pro knihovny MFC Spindial ovládací prvek. Všimněte si, že umístění knihovny DLL MFC je web společnosti Microsoft. Mfc42.cab je k dispozici a podepsaný microsoftem.

```
Contents of spindial.inf:
[mfc42installer]
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0
```

### <a name="the-object-tag"></a>\<Objektu > značky

Následující příklad ukazuje použití `<OBJECT>` značka, které je ukázka ovládacího prvku knihovny MFC Spindial balíček.

```
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">
<PARAM NAME="_Version" VALUE="65536">
<PARAM NAME="_ExtentX" VALUE="2646">
<PARAM NAME="_ExtentY" VALUE="1323">
<PARAM NAME="_StockProps" VALUE="0">
<PARAM NAME="NeedlePosition" VALUE="2">
</OBJECT>
```

V takovém případě spindial.cab bude obsahovat dva soubory, spindial.ocx a spindial.inf. Následující příkaz sestaví soubor CAB:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144` Parametr rezervuje prostor v souboru formátu CAB pro podepisování kódu.

### <a name="the-version-tag"></a>Značka verze

Poznámka: tady `#Version` zadaný soubor CAB informace platí pro ovládací prvek určený *CLASSID* parametr `<OBJECT>` značky.

V závislosti na verzi zadaný můžete vynutit stažení ovládacího prvku. Pro kompletní specifikace `OBJECT` včetně značky *CODEBASE* parametr, viz W3C odkaz.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Označení ovládací prvek bezpečný pro skriptování a inicializaci

Použít na webových stránkách – ovládací prvky ActiveX musí být označené jako bezpečný pro skriptování a inicializaci v případě, že jsou ve skutečnosti bezpečné. Bezpečný ovládací prvek nebude provádět vstupně-výstupních operací disku nebo přímý přístup k paměti nebo registrech počítače.

Ovládací prvky, může být označený jako bezpečný pro skriptování a inicializaci prostřednictvím registru. Upravit `DllRegisterServer` přidat položky podobné následující k označení ovládací prvek jako bezpečné pro skriptování a přetrvávání v registru. Je to alternativní metoda má implementovat `IObjectSafety`.

Identifikátory GUID (globálně jedinečné identifikátory) budou definovat pro ovládací prvek k označení bezpečné pro skriptování a pro trvalost. Ovládací prvky, které může být bezpečně skripty bude obsahovat položku registru, který je podobný následujícímu:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Ovládací prvky, které mohou být inicializovány bezpečně z trvalá data jsou označeny jako bezpečné pro trvalé uložení podobný položky registru:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Přidat položky podobné následující (ID místo nahrazení ovládacího prvku třídy `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) k přidružení klíčů s následujícím ID třídy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a> Problémy s licencí

Pokud chcete použít licencovaného ovládacího prvku na webové stránce, musíte ověřit, že licenční smlouvy umožňuje jeho použití na Internetu a vytvoří soubor balíčku licencí (LPK) se pro něj.

Licencované ovládací prvek ActiveX nenačte správně na stránce HTML Pokud počítači se systémem Internet Explorer není licencován pro použití ovládacího prvku. Například pokud licencovaný ovládací prvek byl vytvořen pomocí jazyka Visual C++, HTML stránku pomocí ovládacího prvku se načte správně na počítači, ve kterém ovládací prvek byl vytvořen, ale nebude načten v jiném počítači, pokud licenční informace.

Použití licencovaného ovládacího prvku ActiveX v Internet Exploreru, musíte zaškrtnout dodavatele licenční smlouvy k ověření, že licence pro ovládací prvek umožňuje:

- Redistribuce

- Použití ovládacího prvku na Internetu

- Použití parametru základu kódu

Použití licencovaného ovládacího prvku na stránce HTML na nonlicensed počítači, musíte vygenerovat soubor balíčku licencí (LPK). Soubor LPK obsahuje licence za běhu pro licencované ovládací prvky na stránce HTML. Tento soubor je generován prostřednictvím LPK_TOOL. Soubor EXE, který se dodává se sadou SDK ActiveX. Další informace najdete v článku na webu MSDN na [ http://msdn.microsoft.com ](http://msdn.microsoft.com).

#### <a name="to-create-an-lpk-file"></a>Vytvořte soubor LPK

1. Spusťte LPK_TOOL. Soubor EXE v počítači, který je licenci k používání ovládacího prvku.

1. V **nástroj pro vytváření licenčního balíčku** v dialogu **dostupné ovládací prvky** pole se seznamem, vyberte každý licencovaný ovládací prvek ActiveX, který se použije na stránce HTML a klikněte na tlačítko **přidat**.

1. Klikněte na tlačítko **uložit Uko & nčení** a zadejte název souboru LPK. Tím vytvoříte LPK soubor a ukončete aplikaci.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Chcete-li vložit licencovaného ovládacího prvku na stránku HTML

1. Upravte stránku HTML. Na stránce HTML vložte \<objektu > značky pro objekt správce licencí před všemi ostatními \<objektu > značky. Správce licencí je ovládací prvek ActiveX, který je nainstalován pomocí aplikace Internet Explorer. ID třídy je uveden níže. Nastavte vlastnost LPKPath objektu správce licencí na cestu a název souboru LPK. Může mít pouze jeden soubor LPK na stránku HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Vložit \<objektu > značky pro licencované ovládací prvek po značce správce licencí.

   Například stránky HTML, který se zobrazí Microsoft maskované upravit ovládací prvek je uveden níže. První třídy, kterou je ID pro ovládací prvek správce licencí, druhá třída ID je pro ovládací prvek maskované úpravy. Upravit značky a přejít na relativní cestu LPK soubor, který jste vytvořili dříve a přidejte značku objektu, včetně ID třídy ovládacího prvku.

1. Vložit \<vložení > atribut pro LPK soubor, pokud používáte modul plug-in NCompass ActiveX.

   Pokud váš ovládací prvek lze zobrazit na jiné aktivní povolené prohlížeče – například Netscape pomocí modulu plug-in NCompass ActiveX – je nutné přidat \<vložení > syntaxe, jak je znázorněno níže.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Další informace o licencování ovládacích prvků naleznete v tématu [ovládací prvky ActiveX: licencování ovládacího prvku ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

##  <a name="_core_signing_code"></a> Podepisování kódu

Podepisování kódu slouží k identifikaci zdrojový kód a zajistit, že kód nebyl změněn od doby byla podepsána. V závislosti na nastavení zabezpečení prohlížeče uživatelé mohou zobrazit upozornění před stažením kódu. Uživatelé se můžou rozhodnout důvěřovat některé vlastníky certifikát nebo společnosti, ve kterých případu kódu jsou podepsány důvěryhodný, stáhnou se bez upozornění. Chcete-li zabránit manipulaci je digitálně podepsaný kód.

Zajistěte, aby že konečný kód je podepsaný tak, aby váš ovládací prvek je automaticky stáhnout bez zobrazení zprávy upozornění vztah důvěryhodnosti. Podrobnosti o tom, jak podepsat kód, naleznete v dokumentaci na Authenticode v sadě SDK ActiveX a najdete v tématu [podepsání souboru CAB](/windows/desktop/devnotes/cabinet-api-functions).

V závislosti na vztahu důvěryhodnosti a Prohlížeč úrovně nastavení zabezpečení může se zobrazit certifikát k identifikaci podpisový osobě nebo firmě. Pokud je úroveň zabezpečení, none nebo vlastník certifikát podepsaný držitelem ovládací prvek je důvěryhodný, certifikát se nezobrazí. Zobrazit [úrovně zabezpečení prohlížeče Internet Explorer a chování ovládacího prvku](#_core_internet_explorer_browser_safety_levels_and_control_behavior) podrobnosti o způsobu nastavení zabezpečení prohlížeče určí, jestli váš ovládací prvek stahován a certifikátu zobrazeného.

Digitální podepisování kódu záruky nezměnil, protože byla podepsána. Hodnota hash kódu je přijatá a vkládat v certifikátu. Tato hodnota hash později ve srovnání s křížkem kódu po stažení kódu, ale před jejím spuštěním. Společnosti, jako je například Verisign, můžete zadat privátní a veřejné klíče potřebné k podepsání kódu. Sada SDK ActiveX se dodává s MakeCert, nástroj pro vytváření testovací certifikáty.

##  <a name="_core_managing_the_palette"></a> Správa palety

Kontejnery určit na paletě a zpřístupní ji jako vedlejší vlastnost **DISPID_AMBIENT_PALETTE**. Kontejner (třeba Internet Explorer) vybere paletu, která se používá ve všech ovládacích prvků ActiveX na stránku k určení vlastní paletu. To zabrání zobrazení blikání a nabízí jednotný vzhled.

Ovládací prvek můžete přepsat `OnAmbientPropertyChange` zpracování oznámení o změnách na paletě.

Ovládací prvek můžete přepsat `OnGetColorSet` vrátit barva nastavena na vykreslení na paletě. Kontejnery používat návratovou hodnotu k určení, zda je ovládací prvek s ohledem na paletě.

V části pravidla OCX 96 ovládací prvek musí vždy dobré si uvědomit svoji paletu na pozadí.

Starší kontejnery, které nepoužívají vlastnost palette okolí bude odesílat zprávy WM_QUERYNEWPALETTE a WM_PALETTECHANGED. Ovládací prvek můžete přepsat `OnQueryNewPalette` a `OnPaletteChanged` zpracovává tyto zprávy.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Úrovně zabezpečení prohlížeče Internet Explorer a chování ovládacího prvku

Prohlížeč obsahuje možnosti pro úroveň zabezpečení, konfigurovatelná uživatelem. Protože webové stránky mohou obsahovat aktivní obsah, který může potenciálně poškodit počítač uživatele, prohlížečů umožňuje uživateli vybrat možnosti pro úroveň zabezpečení. V závislosti na prohlížeči implementuje bezpečný přístup z více úrovní případech ovládacího prvku nemusí vůbec stáhnout nebo se zobrazí certifikát nebo upozornění, aby uživatel mohl zvolte v době běhu, jestli se mají stáhnout ovládací prvek. Chování ovládacích prvků ActiveX v části bezpečnosti vysoká, střední nebo nízké úrovně v Internet Exploreru je uveden níže.

### <a name="high-safety-mode"></a>Režim vysoké zabezpečení

- Ovládací prvky bez znaménka nebudou staženy.

- Podepsané ovládací prvky se zobrazí certifikát, pokud nedůvěryhodné (může uživatel vybrat možnost vždy důvěřovat kód z tohoto vlastníka certifikát od této chvíle).

- Pouze prvky, které jsou označeny jako bezpečné bude mít trvalých dat a/nebo být možné používat skripty.

### <a name="medium-safety-mode"></a>Střední režim

- Ovládací prvky bez znaménka se zobrazí upozornění před stažením.

- Podepsané ovládací prvky se zobrazí certifikát, pokud nedůvěryhodný.

- Nejsou označeny jako bezpečné ovládací prvky se zobrazí upozornění.

### <a name="low-safety-mode"></a>Nízká režim

- Ovládací prvky se stáhnou bez předchozího upozornění.

- Skriptování a stálost dojít bez upozornění.

## <a name="see-also"></a>Viz také

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

