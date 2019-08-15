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
ms.openlocfilehash: 06c39240d3718f6fbaa15b46abeb8ac9132b5945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510863"
---
# <a name="upgrading-an-existing-activex-control"></a>Upgradování existujícího ovládacího prvku ActiveX

Existující ovládací prvky ActiveX (dříve ovládací prvky OLE) lze použít na internetu bez úprav. Můžete však chtít změnit ovládací prvky pro zlepšení výkonu.

> [!IMPORTANT]
> ActiveX je starší verze technologie, která by se neměla používat pro nový vývoj. Další informace o moderních technologiích, které nahrazují prvky ActiveX, naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Při použití ovládacího prvku na webové stránce jsou k dispozici další požadavky. Soubor. ocx a všechny podpůrné soubory musí být na cílovém počítači nebo staženy přes Internet. Díky tomu je velikost kódu a čas stahování důležitým aspektem. Soubory ke stažení lze zabalit do podepsaného souboru. cab. Ovládací prvek můžete označit jako bezpečný pro skriptování a jako bezpečný pro inicializaci.

Tento článek popisuje v následujících tématech:

- [Balení kódu ke stažení](#_core_packaging_code_for_downloading)

- [Označení bezpečného ovládacího prvku pro skriptování a inicializaci](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problémy s licencováním](#_core_licensing_issues)

- [Podpisový kód](#_core_signing_code)

- [Správa palety](#_core_managing_the_palette)

- [Bezpečnostní úrovně a chování ovládacích prvků prohlížeče Internet Exploreru](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Můžete také přidat optimalizace, jak je popsáno v [ovládacích prvcích ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md). Monikery lze použít ke stažení vlastností a velkých objektů BLOB asynchronně, jak je popsáno v [ovládacích prvcích ActiveX na internetu](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a>Balení kódu ke stažení

Další informace o tomto předmětu najdete v tématu [sbalení ovládacích prvků ActiveX](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>Značka ZÁKLADu kódu

Ovládací prvky ActiveX jsou vloženy do webových stránek `<OBJECT>` pomocí značky. `CODEBASE` Parametr`<OBJECT>` značky určuje umístění, ze kterého se má ovládací prvek stáhnout. `CODEBASE`může úspěšně ukazovat na několik různých typů souborů.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Použití tagu CODEBASE se souborem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

Toto řešení stáhne pouze soubor. OCX ovládacího prvku a vyžaduje, aby na klientském počítači byly již nainstalovány všechny podpůrné knihovny DLL. To bude fungovat pro aplikace Internet Explorer a MFC ovládací prvky ActiveX sestavené s jazykem Visual C++, protože aplikace Internet Explorer je dodávána s podpůrnými knihovnami DLL pro vizuální C++ ovládací prvky. Pokud se k zobrazení tohoto ovládacího prvku používá jiný internetový prohlížeč, který podporuje ovládací prvek ActiveX, toto řešení nebude fungovat.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Použití tagu CODEBASE se souborem INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Soubor. inf bude řídit instalaci souboru. ocx a jeho podpůrných souborů. Tato metoda se nedoporučuje, protože není možné podepsat soubor. inf (viz [podpisový kód](#_core_signing_code) pro ukazatele při podepisování kódu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Použití tagu CODEBASE se souborem CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Soubory CAB jsou doporučeným způsobem pro zabalení ovládacích prvků ActiveX, které používají knihovnu MFC. Sbalení ovládacího prvku ActiveX knihovny MFC v souboru CAB umožňuje, aby byl k dispozici soubor. inf pro řízení instalace ovládacího prvku ActiveX a všech závislých knihoven DLL (například knihovny MFC DLL). Použití souboru CAB automaticky komprimuje kód pro rychlejší stažení. Pokud používáte soubor. cab pro stažení součásti, je rychlejší podepsat celý soubor. cab, než každá součást.

### <a name="creating-cab-files"></a>Vytváření souborů CAB

Nástroje pro vytváření souborů CAB jsou teď součástí sady [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Soubor CAB odkazoval na `CODEBASE` by měl obsahovat soubor. ocx pro ovládací prvek ActiveX a soubor. inf pro kontrolu instalace. Soubor CAB vytvoříte tak, že zadáte název řídicího souboru a soubor. inf. Nezahrnujte závislé knihovny DLL, které již mohou existovat v systému v tomto souboru CAB. Knihovny MFC DLL jsou například zabaleny do samostatného souboru CAB a odkazují na soubor s příponou. inf.

Podrobnosti o tom, jak vytvořit soubor CAB, najdete v tématu [Vytvoření souboru CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Soubor INF

Následující příklad, spindial. inf, uvádí podpůrné soubory a informace o verzi potřebné pro ovládací prvek MFC spindial. Všimněte si, že umístění knihoven MFC DLL je web společnosti Microsoft. Mfc42. cab je poskytován a podepsán společností Microsoft.

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

### <a name="the-object-tag"></a>\<Objekt > Značka

Následující příklad znázorňuje použití `<OBJECT>` značky pro zabalení ukázkového ovládacího prvku MFC spindial.

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

V tomto případě bude spindial. cab obsahovat dva soubory, spindial. ocx a spindial. inf. Následující příkaz vytvoří soubor CAB:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144` Parametr rezervuje místo v souboru CAB pro podepisování kódu.

### <a name="the-version-tag"></a>Značka verze

Všimněte si, že `#Version` informace zadané souborem CAB se vztahují k ovládacímu prvku určenému parametrem `<OBJECT>` *ClassID* značky.

V závislosti na zadané verzi můžete vynutit stažení vašeho ovládacího prvku. Úplné specifikace `OBJECT` značky včetně parametru *codebase* naleznete v tématu Reference W3C.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Označení bezpečného ovládacího prvku pro skriptování a inicializaci

Ovládací prvky ActiveX používané na webových stránkách by měly být označeny jako bezpečné pro skriptování a bezpečné pro inicializaci, pokud jsou ve skutečnosti bezpečné. Bezpečný ovládací prvek neprovádí disk v/v nebo přistupuje k paměti nebo registrům přímo v počítači.

Ovládací prvky lze označit jako bezpečné pro skriptování a bezpečné pro inicializaci prostřednictvím registru. Úpravou `DllRegisterServer` můžete přidat položky podobné následujícímu jako k označení ovládacího prvku jako bezpečného pro skriptování a trvalost v registru. Alternativním způsobem je implementace `IObjectSafety`.

Nadefinujete identifikátory GUID (globálně jedinečné identifikátory) pro váš ovládací prvek tak, aby byly označeny jako bezpečné pro skriptování a trvalost. Ovládací prvky, které mohou být bezpečně spouštěny, budou obsahovat položku registru podobnou následující:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Ovládací prvky, které lze bezpečně inicializovat z trvalých dat, jsou označeny jako bezpečné pro stálost s položkou registru podobnou této:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Přidejte položky podobné následujícímu (nahrazení ID třídy ovládacího prvku místo `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) a přidružte ke klíčům následující ID třídy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a>Problémy s licencováním

Pokud chcete použít licencovaný ovládací prvek na webové stránce, musíte ověřit, že licenční smlouva umožňuje použití na internetu a vytvořit soubor balíčku licencí (LPK).

Licencovaný ovládací prvek ActiveX se nebude správně načíst na stránce HTML, pokud počítač, na kterém je spuštěna aplikace Internet Explorer, nemá licenci k použití tohoto ovládacího prvku. Například pokud byl licencovaný ovládací prvek sestaven pomocí vizuálu C++, stránka HTML používající ovládací prvek bude správně načtena v počítači, kde byl ovládací prvek sestaven, ale nebude načten na jiný počítač, pokud nejsou zahrnuty informace o licencování.

Chcete-li použít licencovaný ovládací prvek ActiveX v aplikaci Internet Explorer, je nutné zkontrolovat licenční smlouvu dodavatele a ověřit, že licence pro řízení povolují:

- Redistribuce

- Použití ovládacího prvku na internetu

- Použití parametru CODEBASE

Chcete-li použít licencovaný ovládací prvek na stránce HTML v nelicencovaných počítačích, musíte vygenerovat soubor balíčku licencí (LPK). Soubor LPK obsahuje licence run-time pro licencované ovládací prvky na stránce HTML. Tento soubor se generuje přes LPK_TOOL. EXE, který je součástí sady ActiveX SDK.

#### <a name="to-create-an-lpk-file"></a>Vytvoření souboru LPK

1. Spusťte LPK_TOOL. EXE na počítači, který má licenci k použití ovládacího prvku.

1. V dialogovém okně **Nástroj pro vytváření balíčků licencí** vyberte v seznamu **ovládací prvky k dispozici** všechny licencované ovládací prvky ActiveX, které se použijí na stránce HTML a klikněte na **Přidat**.

1. Klikněte na **uložit & ukončit** a zadejte název souboru LPK. Tím se vytvoří soubor LPK a aplikace se zavře.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Vložení licencovaného ovládacího prvku na stránku HTML

1. Upravte stránku HTML. Na stránce HTML vložte \<objekt > tag pro objekt správce licencí před jakýmikoli jinými \<značkami > objektu. Správce licencí je ovládací prvek ActiveX, který je nainstalován s Internet Explorerem. ID jeho třídy je uvedeno níže. Nastavte vlastnost LPKPath objektu Správce licencí na cestu a název souboru LPK. Můžete mít pouze jeden soubor LPK na stránku HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Po značku správce licencí vložte objekt>značkuprovášlicencovanýovládacíprvek.\<

   Například stránka HTML, která zobrazuje textové pole s maskou Microsoft, je uvedena níže. První ID třídy je pro řízení správce licencí, druhé ID třídy je pro ovládací prvek maskovaná úprava. Změňte značky tak, aby odkazovaly na relativní cestu k souboru. LPK, který jste vytvořili dříve, a přidejte značku objektu, včetně ID třídy pro váš ovládací prvek.

1. Pokud používáte modul plug-in NCompass ActiveX, vložte atribut embed>prosouborLPK.\<

   Pokud je možné ovládací prvek zobrazit na jiných aktivních povolených prohlížečích, například Netscape pomocí modulu plug-in NCompass ActiveX, je nutné přidat \<syntaxi embed >, jak je uvedeno níže.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Další informace o licencování ovládacích prvků naleznete [v tématu ovládací prvky ActiveX: Licencování ovládacího prvku](../mfc/mfc-activex-controls-licensing-an-activex-control.md)ActiveX

##  <a name="_core_signing_code"></a>Podpisový kód

Podepisování kódu je navrženo k identifikaci zdroje kódu a zaručuje, že kód nebyl od svého podepsání změněn. V závislosti na nastavení zabezpečení prohlížeče můžou být uživatelé před stažením kódu upozorněni. Uživatelé se můžou rozhodnout důvěřovat určitým vlastníkům nebo společnostem certifikátů. v takovém případě se kód podepsaný důvěryhodnými uživateli stáhne bez upozornění. Kód je digitálně podepsán, aby nedocházelo k manipulaci.

Ujistěte se, že je váš finální kód podepsaný, aby se váš ovládací prvek mohl automaticky stáhnout bez zobrazení varovných zpráv důvěry. Podrobnosti o tom, jak podepsat kód, najdete v dokumentaci k technologii Authenticode v sadě ActiveX SDK a v tématu [podepisování souboru CAB](/windows/win32/devnotes/cabinet-api-functions).

V závislosti na nastavení důvěryhodnosti a na úrovni zabezpečení prohlížeče se může zobrazit certifikát, který identifikuje podepisující osobu nebo firmu. Pokud je úroveň zabezpečení None nebo pokud je vlastník certifikátu podepsaného ovládacího prvku důvěryhodný, certifikát se nezobrazí. Podrobnosti o tom, jak nastavení zabezpečení prohlížeče určí, zda je váš ovládací prvek stažen a zobrazený certifikát, najdete v části [zabezpečení prohlížeče Internet Exploreru a chování ovládacího prvku](#_core_internet_explorer_browser_safety_levels_and_control_behavior) .

Digitální podpis garantuje, že kód se od svého podepsání nezměnil. Hodnota hash kódu je pořízena a vložena do certifikátu. Tato hodnota hash je později porovnána s hodnotou hash kódu pořízeným po stažení kódu, ale před jeho spuštěním. Společnosti, jako je například VeriSign, můžou poskytovat privátní a veřejné klíče potřebné k podepisování kódu. Sada ActiveX SDK je dodávána s MakeCert, což je nástroj pro vytváření testovacích certifikátů.

##  <a name="_core_managing_the_palette"></a>Správa palety

Kontejnery určují paletu a zpřístupňují je jako vlastnost ambientní **DISPID_AMBIENT_PALETTE**. Kontejner (například Internet Explorer) zvolí paletu, která je používána všemi ovládacími prvky ActiveX na stránce pro určení vlastní palety. Tím zabráníte blikání displeje a zobrazí se konzistentní vzhled.

Ovládací prvek může přepsat `OnAmbientPropertyChange` pro zpracování oznámení o změnách palety.

Ovládací prvek může přepsat `OnGetColorSet` a vrátit sadu barev k vykreslení palety. Kontejnery používají návratovou hodnotu k určení, zda je ovládací prvek s podporou palety.

V rámci pokynů pro OCX 96 musí ovládací prvek vždy realizovat svou paletu na pozadí.

Starší kontejnery, které nepoužívají vlastnost ambientní palety, budou odesílat zprávy WM_QUERYNEWPALETTE a WM_PALETTECHANGED. Ovládací prvek může přepsat `OnQueryNewPalette` a `OnPaletteChanged` zpracovat tyto zprávy.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Bezpečnostní úrovně a chování ovládacích prvků prohlížeče Internet Exploreru

Prohlížeč má možnosti pro úroveň zabezpečení, konfigurovatelné uživatelem. Vzhledem k tomu, že webové stránky mohou obsahovat aktivní obsah, který by mohl poškodit počítač uživatele, prohlížeče umožní uživateli vybrat možnosti pro úroveň zabezpečení. V závislosti na způsobu, jakým prohlížeč implementuje úrovně zabezpečení, nemusí být ovládací prvek vůbec stažen nebo bude zobrazovat certifikát nebo upozornění, aby uživatel mohl zvolit, zda se má ovládací prvek stáhnout. Chování ovládacích prvků ActiveX v oblasti vysoké, střední a nízké úrovně zabezpečení v aplikaci Internet Explorer je uvedeno níže.

### <a name="high-safety-mode"></a>Režim vysoké bezpečnosti

- Nepodepsané ovládací prvky nebudou staženy.

- Pokud nedůvěřujete ovládacím prvkům, zobrazí se certifikát v případě nedůvěryhodného (uživatel může zvolit možnost vždy důvěřovat kódu od tohoto vlastníka certifikátu).

- Pouze ovládací prvky označené jako bezpečné budou mít trvalá data nebo skripty.

### <a name="medium-safety-mode"></a>Režim středního zabezpečení

- Nepodepsané ovládací prvky zobrazí upozornění před stažením.

- Podepsané ovládací prvky zobrazí certifikát v případě nedůvěryhodného.

- Ovládací prvky, které nejsou označeny jako bezpečné, zobrazí upozornění.

### <a name="low-safety-mode"></a>Režim nízké úrovně zabezpečení

- Ovládací prvky se stáhnou bez upozornění.

- Skriptování a trvalá nedochází bez upozornění.

## <a name="see-also"></a>Viz také:

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[MFC – ovládací prvky ActiveX: Licencování ovládacího prvku ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
