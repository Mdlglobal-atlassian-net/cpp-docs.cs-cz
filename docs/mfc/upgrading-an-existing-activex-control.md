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
ms.openlocfilehash: dfee42369b698956f4f91ab61a1f37e0ef06d9f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754515"
---
# <a name="upgrading-an-existing-activex-control"></a>Upgradování existujícího ovládacího prvku ActiveX

Existující ovládací prvky ActiveX (dříve ovládací prvky OLE) lze použít v Síti Internet bez epoš-li. Můžete však chtít upravit ovládací prvky ke zlepšení jejich výkonu.

> [!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Při použití ovládacího prvku na webové stránce existují další důležité informace. Soubor OCX a všechny podpůrné soubory musí být v cílovém počítači nebo musí být staženy přes Internet. Díky velikosti kódu a době stahování důležité úvahy. Soubory ke stažení lze zabalit do podepsaného souboru CAB. Ovládací prvek můžete označit jako bezpečný pro skriptování a jako bezpečný pro inicializaci.

Tento článek popisuje následující témata:

- [Kód balení ke stažení](#_core_packaging_code_for_downloading)

- [Označení ovládacího prvku bezpečné pro skriptování a inicializace](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problémy s licencováním](#_core_licensing_issues)

- [Podpisový kód](#_core_signing_code)

- [Správa palety](#_core_managing_the_palette)

- [Úrovně bezpečnosti prohlížeče internet explorer uvažují a chování ovládacích prvku](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Můžete také přidat optimalizace, jak je popsáno v [ovládacích prvcích ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md). Zástupné názvy lze použít ke stažení vlastností a velkých objektů BLOB asynchronně, jak je popsáno v [ovládacích prvcích ActiveX v Internetu](../mfc/activex-controls-on-the-internet.md).

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>Kód balení ke stažení

Další informace o tomto tématu naleznete [v tématu Packaging ActiveX Controls](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>Značka CODEBASE

Ovládací prvky ActiveX jsou vloženy do webových stránek pomocí značky. `<OBJECT>` Parametr `CODEBASE` značky `<OBJECT>` určuje umístění, ze kterého chcete ovládací prvek stáhnout. `CODEBASE`můžete úspěšně ukazovat na několik různých typů souborů.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Použití značky CODEBASE se souborem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Toto řešení stáhne pouze soubor OCX ovládacího prvku a vyžaduje, aby všechny podpůrné knihovny DLL byly již nainstalovány v klientském počítači. To bude fungovat pro ovládací prvky ActiveX aplikace Internet Explorer a knihovny MFC vytvořené pomocí jazyka Visual C++, protože aplikace Internet Explorer je dodávána s podpůrnými knihovnami DLL pro ovládací prvky Visual C++. Pokud se k zobrazení tohoto ovládacího prvku používá jiný internetový prohlížeč, který je schopen ovládacího prvku ActiveX, nebude toto řešení fungovat.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Použití značky CODEBASE se souborem INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Soubor INF bude řídit instalaci souboru OCX a jeho podpůrných souborů. Tato metoda se nedoporučuje, protože není možné podepsat soubor INF (viz [Podpisový kód](#_core_signing_code) pro ukazatele na podepisování kódu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Použití značky CODEBASE se souborem CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Soubory skříně jsou doporučeným způsobem, jak zabalit ovládací prvky ActiveX, které používají knihovnu MFC. Balení ovládacího prvku ActiveX knihovny MFC do souboru skříně umožňuje zahrnout soubor INF k řízení instalace ovládacího prvku ActiveX a všech závislých knihoven DLL (například knihovny DLL knihovny MFC). Použití souboru CAB automaticky komprimuje kód pro rychlejší stahování. Pokud používáte soubor CAB ke stažení součásti, je rychlejší podepsat celý soubor CAB než jednotlivé součásti.

### <a name="creating-cab-files"></a>Vytváření souborů CAB

Nástroje pro vytváření souborů skříně jsou nyní součástí [sady Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Soubor skříně, na `CODEBASE` který se vztahuje, by měl obsahovat soubor OCX pro ovládací prvek ActiveX a soubor INF pro řízení jeho instalace. Soubor skříně vytvoříte zadáním názvu řídicího souboru a souboru INF. Do tohoto souboru skříně nezahrnčíte závislé knihovny DLL, které již v systému existují. Například knihovny DLL knihovny MFC jsou zabaleny do samostatného souboru skříně a odkazovány řídícím souborem INF.

Podrobnosti o vytvoření souboru CAB naleznete v [tématu Vytvoření souboru CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Soubor INF

V následujícím příkladu spindial.inf jsou uvedeny podpůrné soubory a informace o verzi potřebné pro ovládací prvek Spindial knihovny MFC. Všimněte si, že umístění knihovny DLL knihovny MFC je web společnosti Microsoft. Mfc42.cab je poskytována a podepsána společností Microsoft.

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

### <a name="the-object-tag"></a>Značka \<> OBJECT

Následující příklad ukazuje použití `<OBJECT>` značky k balení ovládacího prvku vzorku Spindial knihovny MFC.

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

V tomto případě spindial.cab bude obsahovat dva soubory, spindial.ocx a spindial.inf. Následující příkaz vytvoří soubor skříně:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Parametr `-s 6144` rezervuje místo ve skříni pro podepisování kódu.

### <a name="the-version-tag"></a>Značka verze

Všimněte si, že `#Version` informace zadané se souborem CAB se vztahuje na ovládací prvek určený parametrem *CLASSID* značky. `<OBJECT>`

V závislosti na zadané verzi můžete vynutit stažení ovládacího prvku. Úplné specifikace `OBJECT` značky včetně parametru *CODEBASE* naleznete v odkazu W3C.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Označení ovládacího prvku bezpečné pro skriptování a inicializace

Ovládací prvky ActiveX používané na webových stránkách by měly být označeny jako bezpečné pro skriptování a bezpečné pro inicializaci, pokud jsou ve skutečnosti bezpečné. Bezpečný ovládací prvek nebude provádět vi disk nebo přístup k paměti nebo registrů počítače přímo.

Ovládací prvky mohou být označeny jako bezpečné pro skriptování a bezpečné pro inicializaci prostřednictvím registru. Upravte `DllRegisterServer` přidání položek podobných následujícím položkám, chcete-li označit ovládací prvek jako bezpečný pro skriptování a trvalost v registru. Alternativní metodou je `IObjectSafety`implementace .

Budete definovat IDENTIFIKÁTORY GUID (globálně jedinečné identifikátory) pro ovládací prvek označit bezpečné pro skriptování a pro trvalost. Ovládací prvky, které lze bezpečně skriptovat, budou obsahovat položku registru podobnou následující:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Ovládací prvky, které lze bezpečně inicializovat z trvalých dat, jsou označeny jako bezpečné pro trvalost s položkou registru podobnou:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Přidejte položky podobné následující (nahrazení id třídy ovládacího `{06889605-B8D0-101A-91F1-00608CEAD5B3}`prvku namísto ) přidružit klíče s následujícím ID třídy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>Problémy s licencováním

Chcete-li na webové stránce použít licencovaný ovládací prvek, je nutné ověřit, zda licenční smlouva umožňuje jeho použití v Internetu, a vytvořit pro něj soubor licenčního balíčku (LPK).

Licencovaný ovládací prvek ActiveX se na stránce HTML nenačte správně, pokud počítač se spuštěnou aplikací Internet Explorer nemá licenci k použití ovládacího prvku. Pokud byl například licencovaný ovládací prvek vytvořen pomocí aplikace Visual C++, stránka HTML pomocí ovládacího prvku se správně načte v počítači, ve kterém byl ovládací prvek vytvořen, ale nebude načítána v jiném počítači, pokud nejsou zahrnuty informace o licencích.

Chcete-li v aplikaci Internet Explorer používat licencovaný ovládací prvek ActiveX, je nutné zkontrolovat licenční smlouvu dodavatele a ověřit, zda licence pro ovládací prvek umožňuje:

- Redistribuce

- Použití ovládacího prvku na internetu

- Použití parametru Základu kódu

Chcete-li použít licencovaný ovládací prvek na stránce HTML v nelicencovaném počítači, musíte vygenerovat soubor licenčního balíčku (LPK). Soubor LPK obsahuje licence za běhu pro licencované ovládací prvky na stránce HTML. Tento soubor je generován prostřednictvím LPK_TOOL. EXE, který je dodáván s sadou ActiveX SDK.

#### <a name="to-create-an-lpk-file"></a>Vytvoření souboru LPK

1. Utíkej LPK_TOOL. EXE v počítači, který je licencován k použití ovládacího prvku.

1. V dialogovém okně **Nástroj pro vytváření licenčních balíčků** vyberte v seznamu Dostupné ovládací **prvky** každý licencovaný ovládací prvek ActiveX, který bude použit na stránce HTML, a klepněte na tlačítko **Přidat**.

1. Klikněte na **Uložit & Konec** a zadejte název souboru LPK. Tím se vytvoří soubor LPK a zavřete aplikaci.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Vložení licencovaného ovládacího prvku na stránku HTML

1. Upravte stránku HTML. Na stránce HTML vložte značku \<> OBJEKT pro objekt \<Správce licencí před jakékoli jiné značky OBJECT>. Správce licencí je ovládací prvek ActiveX, který je nainstalován v aplikaci Internet Explorer. Jeho ID třídy je uvedeno níže. Nastavte vlastnost LPKPath objektu Správce licencí na cestu a název souboru LPK. Na stránku HTML můžete mít pouze jeden soubor LPK.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Za \<značku Správce licencí vložte značku> pro licencovaný ovládací prvek.

   Například stránka HTML, která zobrazuje ovládací prvek Microsoft Mmaskasked Edit, je zobrazena níže. ID první třídy je pro ovládací prvek Správce licencí, ID druhé třídy je pro ovládací prvek Maskované úpravy. Změňte tagy tak, aby ukazovaly na relativní cestu dříve vytvořeného souboru LPK, a přidejte značku objektu včetně ID třídy pro ovládací prvek.

1. Pokud \<používáte modul plug-in NCompass ActiveX, vložte atribut> EMBED pro soubor LPK.

   Pokud lze ovládací prvek zobrazit v jiných prohlížečích s povoleným funkcí Active , musíte přidat syntaxi \<> EMBED, jak je znázorněno níže.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Další informace o licencování ovládacích prvků naleznete [v tématu ActiveX Controls: Licensing an ActiveX Control](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a>Podpisový kód

Podepisování kódu je navrženo tak, aby identifikovalo zdroj kódu a zaručilo, že se kód od podepsání nezměnil. V závislosti na nastavení bezpečnosti prohlížeče mohou být uživatelé před stažením kódu upozorněni. Uživatelé se mohou rozhodnout důvěřovat určitým vlastníkům certifikátů nebo společnostem, v takovém případě bude kód podepsaný důvěryhodnými uživateli stažen bez předchozího upozornění. Kód je digitálně podepsán, aby nedošlo k manipulaci.

Ujistěte se, že je konečný kód podepsán, aby bylo možné ovládací prvek automaticky stáhnout bez zobrazení varovných zpráv důvěryhodnosti. Podrobnosti o tom, jak podepsat kód, naleznete v dokumentaci k authenticode v sadě ActiveX SDK a [v tématu Podepsání souboru CAB](/windows/win32/devnotes/cabinet-api-functions).

V závislosti na nastavení důvěryhodnosti a úrovně bezpečnosti prohlížeče může být zobrazen certifikát k identifikaci osoby nebo společnosti, která podepisuje. Pokud úroveň bezpečnosti není žádná nebo pokud je vlastník certifikátu podepsaného ovládacího prvku důvěryhodný, certifikát se nezobrazí. Podrobnosti o tom, jak nastavení zabezpečení prohlížeče určuje, zda je ovládací prvek stažen a zobrazen certifikát, naleznete v tématu [Úrovně bezpečnosti prohlížeče a chování ovládacího prvku](#_core_internet_explorer_browser_safety_levels_and_control_behavior) v aplikaci Internet Explorer.

Digitální podepisování zaručuje, že kód se od podpisu nezměnil. Hašeř kódu je přijata a vložena do certifikátu. Tato hash je později ve srovnání s hash kódu přijata po stažení kódu, ale před jeho spuštěním. Společnosti jako Verisign mohou dodávat soukromé a veřejné klíče potřebné k podpisu kódu. Sada ActiveX SDK je dodávána s nástrojem MakeCert, který je nástrojem pro vytváření testovacích certifikátů.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>Správa palety

Kontejnery určují paletu a zpřístupňují ji jako vlastnost **okolí, DISPID_AMBIENT_PALETTE**. Kontejner (například Internet Explorer) vybere paletu, která se používá všechny ovládací prvky ActiveX na stránce k určení vlastní palety. Tím se zabrání blikání displeje a představuje konzistentní vzhled.

Ovládací prvek lze `OnAmbientPropertyChange` přepsat zpracovat oznámení o změnách palety.

Ovládací prvek může `OnGetColorSet` přepsat vrátit sadu barev k nakreslení palety. Kontejnery použít vrácenou hodnotu k určení, pokud je ovládací prvek palety.

Podle pokynů OCX 96 musí ovládací prvek vždy realizovat svou paletu na pozadí.

Starší kontejnery, které nepoužívají vlastnost palety okolí, budou odesílat WM_QUERYNEWPALETTE a WM_PALETTECHANGED zprávy. Ovládací prvek můžete `OnQueryNewPalette` `OnPaletteChanged` přepsat a zpracovat tyto zprávy.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Úrovně bezpečnosti prohlížeče internet explorer uvažují a chování ovládacích prvku

Prohlížeč má možnosti pro úroveň bezpečnosti, konfigurovatelné uživatelem. Vzhledem k tomu, že webové stránky mohou obsahovat aktivní obsah, který by mohl poškodit počítač uživatele, umožňují prohlížeče uživateli vybrat možnosti úrovně bezpečnosti. V závislosti na způsobu, jakým prohlížeč implementuje úrovně bezpečnosti, nemusí být ovládací prvek stažen vůbec nebo zobrazí certifikát nebo varovnou zprávu, aby uživatel mohl zvolit za běhu, zda má nebo nemá ovládací prvek stáhnout. Chování ovládacích prvků ActiveX pod vysokou, střední a nízkou úrovní bezpečnosti v aplikaci Internet Explorer je uvedeno níže.

### <a name="high-safety-mode"></a>Režim vysoké bezpečnosti

- Nepodepsané ovládací prvky nebudou staženy.

- Podepsané ovládací prvky zobrazí certifikát, pokud je nedůvěryhodný (uživatel může od nynějška zvolit možnost vždy důvěřovat kódu od tohoto vlastníka certifikátu).

- Pouze ovládací prvky označené jako bezpečné budou mít trvalá data a/nebo budou skriptovatelné.

### <a name="medium-safety-mode"></a>Režim střední bezpečnosti

- Nepodepsané ovládací prvky zobrazí upozornění před stažením.

- Podepsané ovládací prvky zobrazí certifikát, pokud je nedůvěryhodný.

- Ovládací prvky, které nejsou označeny jako bezpečné, zobrazí upozornění.

### <a name="low-safety-mode"></a>Režim nízké bezpečnosti

- Ovládací prvky jsou staženy bez varování.

- Skriptování a trvalosti dojít bez varování.

## <a name="see-also"></a>Viz také

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
