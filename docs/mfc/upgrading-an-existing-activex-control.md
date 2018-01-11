---
title: "Upgradování existujícího ovládacího prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a7b9c76ffd4366522dce366a165698bd3a26173
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="upgrading-an-existing-activex-control"></a>Upgradování existujícího ovládacího prvku ActiveX
Ovládací prvky ActiveX existující (dříve OLE prvky) lze použít na Internetu bez úprav. Můžete však změnit ovládací prvky pro zlepšení výkonu. Při použití ovládacího prvku na webové stránce, existují další aspekty. Soubor .ocx a všechny podpůrné soubory musí být v cílovém počítači nebo stáhnout přes Internet. Díky velikosti kódu a stažení čas důležitý faktor. Stahování se dá zabalit do souboru .cab podepsaný držitelem. Můžete označit ovládací prvek jako bezpečné pro skriptování a jako bezpečné pro inicializaci.  
  
 Tento článek popisuje v následujících tématech:  
  
- [Balení kódu pro stahování](#_core_packaging_code_for_downloading)  
  
- [Označení řízení bezpečné pro skriptování a inicializaci](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [Problémy s licencí](#_core_licensing_issues)  
  
- [Podepisování kódu](#_core_signing_code)  
  
- [Správa palety](#_core_managing_the_palette)  
  
- [Řízení chování a úrovně zabezpečení prohlížeče Internet Explorer](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 Můžete také přidat optimalizace, jak je popsáno v [– ovládací prvky ActiveX: optimalizace](../mfc/mfc-activex-controls-optimization.md). Monikery lze stáhnout vlastnosti a velké objekty BLOB asynchronně, jak je popsáno v [ActiveX – ovládací prvky na Internetu](../mfc/activex-controls-on-the-internet.md).  
  
##  <a name="_core_packaging_code_for_downloading"></a>Balení kódu pro stahování  
 Další informace o této problematice naleznete v článku znalostní báze Knowledge Base "Balení MFC – ovládací prvky pro použití přes Internet" (Q167158). Můžete najít články znalostní báze Knowledge Base na [http://support.microsoft.com/support](http://support.microsoft.com/support).  
  
### <a name="the-codebase-tag"></a>CODEBASE značky  
 ActiveX – ovládací prvky jsou vloženy do webových stránek pomocí `<OBJECT>` značky. `CODEBASE` Parametr `<OBJECT>` značka udává umístění, ze kterého mají být staženy ovládacího prvku. `CODEBASE`může ukazovat na mnoha různých typech souborů úspěšně.  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Pomocí značky CODEBASE se souborem OCX  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 Toto řešení stáhne pouze soubory .ocx ovládacího prvku a vyžaduje všechny podpůrné knihoven DLL pro již nainstalované v klientském počítači. To bude fungovat pro Internet Explorer a MFC ActiveX – ovládací prvky vytvořené s nástroji Visual C++, protože aplikace Internet Explorer je dodáván s podpůrné knihovny DLL pro ovládací prvky jazyka Visual C++. Pokud jiný internetový prohlížeč, který je podporuje ovládací prvek ActiveX se používá k zobrazení tohoto ovládacího prvku, toto řešení nebude fungovat.  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>Pomocí značky CODEBASE soubor INF  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 Soubor s příponou INF bude řídit instalaci .ocx a jeho podpůrné soubory. Tato metoda se nedoporučuje, protože není možné k podepsání souboru .inf (viz [podepisování kódu](#_core_signing_code) pro ukazatele na podepisování kódu).  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>Pomocí značky CODEBASE soubor CAB  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 Soubory CAB jsou doporučeným způsobem balíček ovládací prvky ActiveX, které používají MFC. Balení ovládacího prvku ActiveX knihovny MFC v souboru CAB umožňuje soubor s příponou INF mají být zahrnuty do ovládacího prvku instalace ovládacího prvku ActiveX a všechny závislé knihoven DLL (například MFC DLL). Pomocí souboru CAB automaticky komprimuje kódu pro rychlejší stahování. Pokud používáte soubor .cab pro součástí ke stažení, je rychlejší k podepsání souboru CAB celý než jednotlivých součástí.  
  
### <a name="creating-cab-files"></a>Vytváření souborů CAB  
 Soubor CAB Development Kit si můžete stáhnout z článku znalostní báze [310618: Microsoft soubor CAB Software Development Kit](http://go.microsoft.com/fwlink/p/?linkid=148204). V této sadě zjistíte nástroje potřebné k vytvoření souborů CAB.  
  
 Soubor CAB na kterou odkazuje `CODEBASE` by měly obsahovat soubor .ocx pro ovládací prvek ActiveX a soubor s příponou INF k řízení jeho instalace. Vytvoříte soubor CAB tak, že zadáte název řídicí soubor a soubor s příponou INF. Nezahrnujte závislé knihovny DLL, které možná již existuje v systému v tomto souboru CAB. Knihovny MFC DLL jsou například zabalené do samostatného souboru CAB a řízení soubor INF.  
  
 Podrobnosti o tom, jak vytvořit soubor CAB najdete v tématu [vytváření souboru CAB](http://msdn.microsoft.com/en-us/cc52fd09-bdf6-4410-a693-149a308f36a3).  
  
### <a name="the-inf-file"></a>Soubor INF  
 Následující příklad, spindial.inf, seznamy podpůrné soubory a informace o verzi potřebné pro MFC Spindial řízení. Všimněte si, že umístění knihovny MFC DLL je webu společnosti Microsoft. Mfc42.cab dodána a podepsán společností Microsoft.  
  
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
  
### <a name="the-object-tag"></a>\<OBJEKT > značky  
 Následující příklad ilustruje, pomocí `<OBJECT>` značka do balíčku ovládacího prvku MFC Spindial ukázka.  
  
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
  
 V takovém případě spindial.cab bude obsahovat dva soubory, spindial.ocx a spindial.inf. Následující příkaz vytvoří soubor CAB:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `-s 6144` Parametr rezervy místa v souboru CAB pro podepisování kódu.  
  
### <a name="the-version-tag"></a>Verze značky  
 Všimněte si zde, že `#Version` informace zadaný soubor CAB se vztahují k ovládacímu prvku určeného `CLASSID` parametr `<OBJECT>` značky.  
  
 V závislosti na verzi zadaný můžete vynutit stažení ovládacího prvku. Pro dokončení specifikace `OBJECT` včetně značky `CODEBASE` parametr a referenční dokumentace najdete W3C.  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Označení řízení bezpečné pro skriptování a inicializaci  
 Ovládací prvky ActiveX, které používají ve webových stránkách by měl být označen jako bezpečné pro skriptování a inicializaci, pokud jsou ve skutečnosti bezpečné. Bezpečné ovládací prvek nebude provádět v/v disku nebo přístup k paměti nebo registry počítače.  
  
 Ovládací prvky můžete označit jako bezpečné pro skriptování a inicializaci prostřednictvím registru. Upravit `DllRegisterServer` přidat položky podobné následující k označení prvku jako bezpečné pro skriptování a trvalost v registru. Je to alternativní metoda je implementace `IObjectSafety`.  
  
 Určíte identifikátory GUID (globálně jedinečné identifikátory) pro ovládací prvek označit bezpečné pro skriptování a trvalost. Ovládací prvky, které můžete bezpečně skriptovány bude obsahovat položku registru, který je podobný následujícímu:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Ovládací prvky, které může být bezpečně inicializována z trvalých dat jsou označeny jako bezpečné pro trvalost s položkou registru podobně jako:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Přidat položky podobné následující (ID místě nahraďte ovládacího prvku třídy `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) Chcete-li přidružit klíče s následujícím ID třídy:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a>Problémy s licencí  
 Pokud chcete použít licencovanou ovládacího prvku na webové stránce, je nutné ověřit, že licenční smlouva umožňuje jeho použití na Internetu a vytvoření souboru (LPK) pro něj.  
  
 Licencované ovládací prvek ActiveX nebude správně načíst na stránce HTML, pokud počítači aplikace Internet Explorer nemá licenci pro používání ovládacího prvku. Například pokud licencované ovládací prvek byl vytvořený pomocí Visual C++, stránky HTML pomocí ovládacího prvku načte správně v počítači, kde byl sestaven ovládacího prvku, ale nebude načtena v jiném počítači, pokud jsou zahrnuty licenční informace.  
  
 Chcete-li použít licencované ovládací prvek ActiveX v Internet Exploreru, je třeba zkontrolovat dodavatele licenční smlouvy k ověření, že licence pro ovládací prvek povoluje:  
  
-   Redistribuce  
  
-   Použití ovládacího prvku na Internetu  
  
-   Použití parametru základu kódu  
  
 Chcete-li použít licencované ovládací prvek na stránce HTML na nonlicensed počítači, musíte vygenerovat souboru (LPK). Soubor LPK obsahuje běhu licencí pro licencované ovládací prvky na stránce HTML. Tento soubor je generována pomocí LPK_TOOL. Soubor EXE, který se dodává s ActiveX SDK. Další informace najdete v článku na webu MSDN na [http://msdn.microsoft.com](http://msdn.microsoft.com).  
  
#### <a name="to-create-an-lpk-file"></a>Vytvořit soubor LPK  
  
1.  Spusťte LPK_TOOL. EXE v počítači, který má licenci, použijte ovládací prvek.  
  
2.  V **nástroj pro tvorbu licenční balíček** dialogovém **dostupných ovládacích prvků** pole se seznamem, vyberte každý licencované ovládací prvek ActiveX, který se použije na stránce HTML a klikněte na tlačítko **přidat**.  
  
3.  Klikněte na tlačítko **uložit a ukončete** a zadejte název souboru LPK. Tato akce vytvoří LPK soubor a ukončete aplikaci.  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Chcete-li vložit licencované ovládací prvek na stránce HTML  
  
1.  Upravte stránku HTML. Na stránce HTML vložit \<OBJEKT > značky pro objekt správce licencí před všemi ostatními \<OBJEKT > značky. Správce licencí je ovládací prvek ActiveX, který je nainstalován pomocí Internet Exploreru. Jeho ID třídy je uveden níže. Nastavte vlastnost LPKPath objektu správce licencí na cestu a název souboru LPK. Můžete mít jenom jeden soubor LPK pro stránku HTML.  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  Vložit \<OBJEKT > značky pro licencované ovládací prvek po značce správce licencí.  
  
     Například stránky HTML, která zobrazí ovládací prvek maskované úpravy Microsoft jsou uvedeny níže. První třídy, na kterou je ID pro ovládací prvek správce licencí, sekundu třídy, na kterou je ID pro ovládací prvek maskované úpravy. Změňte značky tak, aby odkazoval na relativní cestu k souboru LPK, které jste vytvořili dříve a přidání značka object, včetně ID třídy pro vlastní ovládací prvek.  
  
3.  Vložit \<vložení > atribut souboru LPK, pokud používáte modul plug-in NCompass ActiveX.  
  
     Pokud vaše řízení lze zobrazit v dalších aktivní povolené prohlížeče – například Netscape pomocí modulu plug-in NCompass ActiveX – je nutné přidat \<vložení > syntaxe, jak je uvedeno níže.  
  
 ```  
 <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
 
 <EMBED SRC = "maskedit.LPK">  
 
 </OBJECT>  
 <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
 </OBJECT>  
 ```  
  
 Další informace o licencích řízení, najdete v části [– ovládací prvky ActiveX: licencování ovládacích prvků ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
##  <a name="_core_signing_code"></a>Podepisování kódu  
 Podepisování kódu slouží k identifikaci zdrojového kódu a zaručit, že se od jeho nezměnil kód byl podepsán. V závislosti na nastavení zabezpečení prohlížeče uživatelé mohou se zobrazit upozornění před stažením kódu. Uživatelé mohou zvolit za určité vlastníky certifikát nebo společnosti, ve kterých případu kód podepsaný tyto důvěryhodné, budou staženy bez upozornění. Aby se zabránilo zneužití digitálně podepsaný kód.  
  
 Zajistěte, aby že konečné kódu je podepsaný tak, aby vlastní ovládací prvek lze automaticky stáhnout bez zobrazení zprávy upozornění vztah důvěryhodnosti. Podrobnosti o tom, jak podepsat kód, naleznete v dokumentaci na Authenticode v sadě SDK ActiveX a najdete v tématu [podepsání souboru CAB](http://msdn.microsoft.com/en-us/04d8b47a-8f1c-4b54-ab90-730fcdc03747).  
  
 V závislosti na vztahu důvěryhodnosti a Prohlížeč úrovně nastavení zabezpečení může se zobrazit certifikát k identifikaci podpisový osobě nebo firmě. Pokud úroveň zabezpečení je none, nebo pokud je vlastník certifikát podepsaný držitelem ovládacího prvku důvěryhodný, certifikát se nezobrazí. V tématu [úrovně zabezpečení prohlížeče Internet Explorer a řídit chování](#_core_internet_explorer_browser_safety_levels_and_control_behavior) podrobnosti o tom, jak nastavení zabezpečení prohlížeče určí, zda stáhne vlastního ovládacího prvku a certifikát zobrazí.  
  
 Digitální podepisování kódu záruky nebylo změněno vzhledem k tomu, že je podepsaný. Hodnota hash kód je přijatá a vkládat v certifikátu. Tato hodnota hash se později porovná se hodnota hash kód prováděné po stažení kód, ale před jeho spuštěním. Společnosti, jako je například Verisign může poskytovat privátní a veřejné klíče, které jsou potřebné pro podepsání kódu. Sada SDK ActiveX se dodává s MakeCert, nástroj pro vytváření testovací certifikáty.  
  
##  <a name="_core_managing_the_palette"></a>Správa palety  
 Kontejnery určit palety a zpřístupní ji jako vedlejší vlastnost, **DISPID_AMBIENT_PALETTE**. Kontejner (například Internet Explorer) zvolí palety, který je používán všechny ovládací prvky ActiveX na stránce určit vlastní paletu. Tím se zabrání zobrazení blikání a uvede konzistentní vzhled.  
  
 Můžete přepsat ovládacího prvku `OnAmbientPropertyChange` pro zpracování oznámení o změnách paletě.  
  
 Můžete přepsat ovládacího prvku `OnGetColorSet` vrátit barvu nastavit k vykreslení paletě. Kontejnery pomůže určit, zda je ovládací prvek podporující palety návratovou hodnotu.  
  
 V části OCX 96 pokyny ovládacího prvku musí vždy Uvědomte si, jeho palety na pozadí.  
  
 Odešle starší kontejnery, které nepoužívají vlastnost palette vedlejším `WM_QUERYNEWPALETTE` a `WM_PALETTECHANGED` zprávy. Můžete přepsat ovládacího prvku `OnQueryNewPalette` a `OnPaletteChanged` pro zpracování těchto zpráv.  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Řízení chování a úrovně zabezpečení prohlížeče Internet Explorer  
 Prohlížeč obsahuje možnosti pro úroveň zabezpečení, konfigurovatelná uživatelem. Protože webové stránky může obsahovat aktivní obsah, který může potenciálně poškodit počítač uživatele prohlížečů umožňuje uživateli vybrat možnosti pro úroveň zabezpečení. V závislosti na způsobu, prohlížeč implementuje úrovně zabezpečení ovládacího prvku nemusí vůbec stáhnout, nebo se zobrazí certifikát nebo upozornění chcete umožnit uživatelům zvolit za běhu, zda ke stažení ovládacího prvku. Níže je uveden seznam chování ovládacích prvků ActiveX v části zabezpečení Vysoká, střední a nízké úrovně v Internet Exploreru.  
  
### <a name="high-safety-mode"></a>Režim vysoké zabezpečení  
  
-   Nepodepsané ovládací prvky, nebudou staženy.  
  
-   Podepsané ovládací prvky zobrazí certifikát, pokud nedůvěryhodná (uživatel může zvolit možnost vždy důvěřovat kód z tohoto vlastníka certifikát od této chvíle).  
  
-   Jenom prvky, které jsou označeny jako bezpečné bude trvalých dat nebo být možné používat skripty.  
  
### <a name="medium-safety-mode"></a>Režim střední úroveň zabezpečení  
  
-   Nepodepsané ovládací prvky se zobrazí upozornění před stažením.  
  
-   Pokud nedůvěryhodná zobrazí podepsané ovládací prvky certifikát.  
  
-   Ovládací prvky nejsou označeny jako bezpečné se zobrazí upozornění.  
  
### <a name="low-safety-mode"></a>Režim nízké zabezpečení  
  
-   Ovládací prvky se stáhnou bez upozornění.  
  
-   Skriptování a trvalost dojít bez upozornění.  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování MFC](../mfc/mfc-internet-programming-basics.md)   
 [MFC – ovládací prvky ActiveX: Licencování ovládacích prvků ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

