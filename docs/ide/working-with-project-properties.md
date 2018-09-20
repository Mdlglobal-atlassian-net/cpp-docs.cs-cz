---
title: Práce s vlastnostmi projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project properties [C++], modifying
- properties [C++]
- Visual C++ projects, properties
- projects [C++], properties
ms.assetid: 9b0d6f8b-7d4e-4e61-aa75-7d14944816cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85439e191ac8676603c9d7fab8a41bb126e97b9e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398661"
---
# <a name="working-with-project-properties"></a>Práce s vlastnostmi projektu

V integrovaném vývojovém prostředí, všechny informace potřebné k sestavení projektu vystavena jako *vlastnosti*. Tyto informace zahrnují název aplikace, rozšíření (například knihovny DLL, LIB, EXE), možnosti kompilátoru, možnosti linkeru, nastavení ladicího programu, vlastní kroky sestavení a mnoha dalším věcem. Obvykle použijete *stránky vlastností* ( **projektu &#124; vlastnosti**) k zobrazení a úpravě těchto vlastností.

Při vytváření projektu systém přiřadí hodnoty pro různé vlastnosti. Výchozí hodnoty lišit v závislosti na typu projektu a jaké možnosti můžete vybrat v Průvodci vytvořením aplikace. Například projekt knihovny ATL má vlastnosti týkající se souborů MIDL, ale tyto chybí v základní Konzolová aplikace. Výchozí vlastnosti jsou uvedeny v podokně obecné na stránkách vlastností:

![Visual C&#43; &#43; výchozích hodnot projektu](../ide/media/visual-c---project-defaults.png "výchozí nastavení projektu Visual C++")

Některé vlastnosti, jako je například název aplikace, platí pro všechny varianty sestavení, bez ohledu na cílovou platformu nebo zda je sestavení ladění nebo vydání. Ale většinu vlastností jsou závislé na konfiguraci. Je to proto, že má kompilátor vědět, jaké konkrétní platformy, se bude program spouštět v a jaké kompilátoru specifické možnosti použít, aby bylo možné generovat správný kód. Proto když nastavíte vlastnost, je důležité věnovat pozornost tomu, jaké konfigurace a platforma má použít novou hodnotu. By se měly používat jenom k sestavení ladění Win32, nebo by to platí také pro ladění ARM a ladění x64? Například **optimalizace** , ve výchozím nastavení, je nastavena na **maximalizovat rychlost (/ O2)** v konfiguraci vydané verze, ale je zakázané v konfiguraci ladění.

Stránky vlastností jsou navržené tak, aby se vždy zobrazí, a v případě potřeby upravit, které konfigurace a platforma hodnotu vlastnosti by se měly používat pro. Následující obrázek znázorňuje stránky vlastností s informacemi o platformy a konfigurace v seznamu polí v horní části. Když **optimalizace** vlastnost zde není nastavena, bude platit pouze pro ladění Win32 sestavení, který aktivní konfiguraci, jak je znázorněno red šipek.

![Visual C&#43; &#43; aktivní konfigurace pro zobrazení stránky vlastností](../ide/media/visual-c---property-pages-showing-active-configuration.png "aktivní konfigurace pro zobrazení stránky vlastností Visual C++")

Následující obrázek ukazuje stejné stránce vlastností projektu, ale konfigurace se změnil na vydání. Všimněte si jinou hodnotu pro vlastnost optimalizace. Všimněte si také, že je aktivní konfiguraci stále ladit. Můžete nastavit vlastnosti pro žádnou konfiguraci. nemusí být aktivní.

![Visual C&#43; &#43; konfigurace vydání zobrazení stránky vlastností](../ide/media/visual-c---property-pages-showing-release-config.png "konfigurace vydání zobrazení stránky vlastností Visual C++")

Samotný systém projektu je založené na MSBuild, který definuje formáty souborů a pravidla pro vytváření projektů z jakéhokoli druhu. Nástroj MSBuild spravuje řadu složitost vytváření pro více konfigurací a platforem, ale je třeba porozumět ještě něco o tom, jak funguje. To je obzvláště důležité, pokud chcete definovat vlastní konfigurace nebo vytvářet opakovaně použitelné sady vlastností, které můžete sdílet a importovat do více projektů.

Vlastnosti projektu jsou uloženy přímo v souboru projektu (*.vcxproj) nebo v jiných souborech XML nebo .props importuje soubor projektu a který poskytnout výchozí hodnoty. Jak je uvedeno výše, může být přiřazen jinou hodnotu v různých souborů stejnou vlastnost pro stejnou konfiguraci. Při sestavování projektu stroji MSBuild engine vyhodnotí jako soubor projektu a všechny importované soubory v dobře definovaných pořadí (popsaných níže). Jak se vyhodnotí každého souboru, všechny hodnoty vlastností, které jsou definované v tomto souboru přepíše existující hodnoty. Všechny hodnoty, které nejsou zadané se dědí ze souborů, které byly dříve vyhodnoceny. Proto když nastavíte vlastnost s použitím stránek vlastností, je také důležité věnovat pozornost tomu, kde nastavujete. Pokud vlastnost nastavíte na "X" v souboru .props, ale vlastnost je nastavena na "Y" v souboru projektu, projekt bude sestaven s nastavenou na "Y". Pokud stejnou vlastnost nastavená na "Z" na položku projektu, jako je například soubor .cpp, stroji MSBuild engine použije hodnotu "Z". Další informace najdete v tématu [dědičnosti vlastností](#bkmkPropertyInheritance) dále v tomto článku.

## <a name="build-configurations"></a>Konfigurace sestavení

Konfigurace je právě libovolného skupiny vlastností, které je přiřazen název. Visual Studio poskytuje konfigurace Debug a Release a každý nastaví různé vlastnosti pro sestavení pro ladění nebo sestavení pro vydání. Můžete použít **nástroje Configuration Manager** definovat vlastní konfigurace jako pohodlný způsob, jak vlastnosti skupiny pro konkrétní charakter sestavení. Správce vlastností se používá pro pokročilé práce s vlastnostmi, ale jeho protože pomáhá vizualizovat konfigurace vlastností zavedeme tady. Přístup z **zobrazení &#124; Správce vlastností** nebo **zobrazení &#124; ostatní Windows &#124; Správce vlastností** v závislosti na nastavení. V projektu má uzlů pro každý pár konfigurace a platformy. U každého z těchto uzlů jsou uzly pro seznamy vlastností (souborech .props), které nastavit některé specifické vlastnosti pro tuto konfiguraci.

![Správce vlastností](../ide/media/property-manager.png "Správce vlastností")

Pokud přejděte do podokna obecné na stránkách vlastností (viz předchozí obrázek) a nastavte vlastnost znaková sada na "Nenastaveno" místo "Použití Unicode" a klikněte na tlačítko **OK**, zobrazí se Správce vlastností žádné **Podpora kódování Unicode** vlastností pro aktuální konfiguraci, ale stále bude existuje další konfigurace.

Další informace o Správci vlastností a vlastností najdete v tématu [vytváření opakovaně použitelných vlastností konfigurací](#bkmkPropertySheets) dále v tomto článku.

> [!TIP]
> Soubor .user je starší verze funkce a doporučujeme odstranit aby bylo možné zachovat vlastnosti správně seskupeny podle konfigurace a platformy.

## <a name="target-platforms"></a>Cílové platformy

*Cílová platforma* odkazuje na typ zařízení a/nebo operační systém, který se spustí spustitelný soubor na. Můžete vytvářet projekt pro více než jednu platformu. Dostupné cílové platformy pro projekty C++ závisí na typu projektu. zahrnout, ale nejsou omezeny na Win32, x64, ARM, Android a iOS.     **X86** cílové platformy, který můžete vidět v **nástroje Configuration Manager** je stejný jako **Win32** v nativních projektů C++. Win32 znamená Windows 32-bit a **x64** znamená Windows 64-bit. Další informace o těchto dvou platforem, naleznete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).

**Jakýkoli procesor** cílové platformy hodnoty, který můžete vidět v **nástroje Configuration Manager** nemá žádný vliv na nativních projektů C++; je relevantní pro C + +/ CLI a dalších .NET typy projektů. Další informace najdete v tématu [/CLRIMAGETYPE (zadat typ z bitové kopie modulu CLR)](../build/reference/clrimagetype-specify-type-of-clr-image.md).

## <a name="property-pages"></a>Stránky vlastností

Jak bylo uvedeno dříve, systém projektu Visual C++ je založen na [MSBuild](/visualstudio/msbuild/msbuild-properties) a hodnoty jsou uloženy v souboru projektu XML výchozí .props a .targets soubory. Pro Visual Studio 2015, tyto soubory jsou umístěny v **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Pro Visual Studio 2017, tyto soubory jsou umístěny v  **\\Program Files (x86)\\sady Microsoft Visual Studio\\2017\\_edition_\\Common7\\ Integrované vývojové prostředí\\VC\\VCTargets**, kde _edition_ je nainstalované verze sady Visual Studio. Vlastnosti jsou také uloženy v jakékoli vlastní souborech, které můžete přidat na svůj projekt. Důrazně doporučujeme, že není upravíte tyto soubory ručně a místo toho použijte stránky vlastností v prostředí IDE k úpravě všech vlastností, zejména těch, které se účastní dědičnosti, pokud nemáte velmi dostatečné povědomí o MSBuild.

Následující obrázek znázorňuje stránky vlastností projektu jazyka Visual C++. V levém podokně **adresáře VC ++** *pravidlo* je vybraná, a v pravém podokně je uveden seznam vlastností, které jsou spojeny s tímto pravidlem. `$(...)` Hodnoty se nazývají bohužel *makra*. Jedná se o *není* makra jazyka C/C++, ale jednoduše kompilace konstanty. Makra jsou popsány v [makra stránky vlastností](#bkmkPropertiesVersusMacros) části dále v tomto článku.)

![Stránky vlastností projektu](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")

> [!WARNING]
> **Společné vlastnosti** konfigurace v dřívějších verzích sady Visual Studio se odebraly. Přidání odkazu na projekt, můžete nyní použít **přidat odkaz** dialogového okna v stejným způsobem jako u spravované jazyky. Zobrazit [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).

#### <a name="to-set-a-property-for-a-project"></a>Nastavení vlastnosti projektu

1. Pro většinu scénářů můžete nastavit vlastnosti na úrovni projektu bez vytváření vlastních vlastností. V hlavní nabídce zvolte **projektu &#124; vlastnosti**, nebo klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolte **vlastnosti**.

2. Použití **konfigurace** a **platformy** seznamu v horní části dialogového okna k určení, které vlastnosti skupiny by se měly používat vaše změny. V mnoha případech **všechny platformy** a **všechny konfigurace** jsou správnou volbou. Chcete-li nastavit vlastnosti pro pouze některé konfigurace, vyberte je v **Správce vlastností**a pak otevřete místní nabídku a zvolte **vlastnosti**.

**Stránky vlastností** dialogové okno zobrazuje pouze stránky vlastností, které se vztahují k aktuálnímu projektu. Pokud například projekt nemá soubor .idl, stránka s vlastnostmi MIDL se nezobrazí.

Když zvýrazníte vlastnosti na stránce vlastností, můžete stisknout **F1** přejít v referenčním tématu pro další informace o odpovídajícího přepínače kompilátoru nebo linkeru.

Další informace o každou stránku vlastností najdete v těchto tématech:

- [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md)

- [Obecná stránka vlastností (soubor)](../ide/general-property-page-file.md)

- [Stránky vlastností příkazového řádku](../ide/command-line-property-pages.md)

- [Nastavení projektu pro konfiguraci ladění jazyka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)

- [NMake – stránka vlastností](../ide/nmake-property-page.md)

- [Stránky vlastností linkeru](../ide/linker-property-pages.md)

- [Stránky vlastností prostředků](../ide/resources-property-pages.md)

- [MIDL – stránky vlastností](../ide/midl-property-pages.md)

- [Stránka vlastností webových odkazů](../ide/web-references-property-page.md)

- [Stránka vlastností nástroje Generátor dat XML](../ide/xml-data-generator-tool-property-page.md)

## <a name="to-quickly-browse-and-search-all-properties"></a>Rychlé procházení a vyhledávání všechny vlastnosti

**Všechny možnosti** stránka vlastností (v části **vlastnosti konfigurace &#124; C/C++** uzlu v **stránky vlastností** dialogové okno) nabízí rychlý způsob procházení a vyhledávání vlastnosti, které jsou k dispozici v aktuálním kontextu. Obsahuje speciální vyhledávací pole s jednoduchou syntaxí umožňující filtrovat výsledky:

Bez předpony:<br/>
Prohledávat pouze názvy vlastností (podřetězec bez rozlišení velkých a malých písmen)

'/' nebo '-':<br/>
Prohledávat pouze přepínače kompilátoru (předpona nerozlišující velká a malá písmena)

v:<br/>
Prohledávat pouze hodnoty (podřetězec bez rozlišení velkých a malých písmen)

##  <a name="bkmkPropertiesVersusMacros"></a> Makra stránky vlastností

A *– makro* kompilace konstanta, která může odkazovat na hodnotu, která je definována pomocí sady Visual Studio nebo systém MSBuild, nebo hodnotu definovanou uživatelem. Použijete-li makra namísto pevně definovaných hodnot, jako jsou například cesty k adresářům, můžete snadněji sdílet nastavení vlastností mezi počítači a mezi verzemi sady Visual Studio a lépe tak zajistit, aby se nastavení projektu řádně zapojilo do dědičnosti vlastností. Chcete-li zobrazit hodnoty všech dostupných maker slouží Editor vlastností.

### <a name="predefined-macros"></a>Předdefinovaná makra

*globální makra*<br/>
Platí pro všechny položky v konfiguraci projektu. Má syntaxi `$(name)`. Příkladem globálního makra je `$(VCInstallDir)`, který ukládá do kořenového adresáře instalace sady Visual Studio. Globální makro odpovídá `PropertyGroup` v nástroji MSBuild.

*makra položky*<br/>
Má syntaxi `%(name)`. U souboru je makro položky platné pouze pro daný soubor – můžete například použít `%(AdditionalIncludeDirectories)` k určení adresářů souborů, které platí pouze pro určitý soubor k zahrnutí. Tento druh položky makro odpovídá `ItemGroup` metadat v nástroji MSBuild. Pokud se používá v kontextu konfigurace projektu, platí makro položky pro všechny soubory určitého typu. Například C/C++ **Definice preprocesoru** vlastnost konfigurace `%(PreprocessorDefinitions)` makro položky, která se vztahuje na všechny soubory .cpp v projektu. Tento druh položky makro odpovídá `ItemDefinitionGroup` metadat v nástroji MSBuild. Další informace najdete v tématu [definice položek](/visualstudio/msbuild/item-definitions).

### <a name="user-defined-macros"></a>Uživatelská makra

Můžete vytvořit *uživatelská makra* pro použití jako proměnných při sestavování projektu. Můžete například vytvořit uživatelem definované makro poskytující hodnotu pro vlastní krok sestavení nebo pro vlastní nástroj sestavení. Uživatelem definované makro je pár název/hodnota. V souboru projektu, použijte **$(**<em>název</em>**)** zápisu pro přístup k hodnotě.

Uživatelem definované makro je uloženo v seznamu vlastností. Pokud váš projekt zatím neobsahuje seznam vlastností, můžete vytvořit podle pokynů v části [vytváření opakovaně použitelných vlastností konfigurací](#bkmkPropertySheets).

##### <a name="to-create-a-user-defined-macro"></a>Vytvoření uživatelem definovaného makra

1. V **Správce vlastností** okna (v řádku nabídek zvolte **zobrazení**, **Správce vlastností**), otevřete místní nabídku pro seznam vlastností (název má koncovku .user) a klikněte na tlačítko Vlastnosti. **Stránky vlastností** otevře se dialogové okno pro tento seznam vlastností.

1. V levém podokně dialogového okna, vyberte **uživatelská makra**. V pravém podokně, vyberte **přidat makro** tlačítko Otevřít **přidat uživatelské makro** dialogové okno.

1. V dialogovém okně zadejte název a hodnotu makra. Volitelně můžete vybrat **nastavit toto makro jako proměnnou prostředí v prostředí pro sestavení** zaškrtávací políčko.

## <a name="property-editor"></a>Editor vlastností

Editor vlastností můžete použít ke změně některých vlastností řetězce a k výběru maker jako hodnot. Editor vlastností otevřete tak, že vyberete vlastnost na stránce vlastností a pak kliknete na šipku dolů na pravé straně. Pokud rozevírací seznam obsahuje  **\<Upravit >**, pak je můžete ji vybrat a zobrazit tak Editor vlastností pro danou vlastnost.

![Vlastnost&#95;Editor&#95;rozevírací seznam](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")

V editoru vlastností můžete použít **makra** tlačítko Zobrazit dostupná makra a jejich aktuálními hodnotami. Následující ilustrace zobrazuje Editor vlastností pro **další adresáře souborů k zahrnutí** vlastnost po **makra** výběru tlačítka. Když **Zdědit z nadřazené nebo projektu výchozí** zaškrtávací políčko zaškrtnuto a přidáte novou hodnotu, připojí se ke všem hodnotám, které jsou aktuálně děděny. Pokud zaškrtnutí políčka zrušíte, nahradí nová hodnota zděděné hodnoty. Ve většině případů ponechte políčko zaškrtnuté.

![Editor vlastností, Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")

##  <a name="bkmkPropertySheets"></a> Vytváření opakovaně použitelných vlastností konfigurací

Je možné nastavit rovněž „globální“ vlastnosti podle jednotlivých uživatelů nebo počítačů, nadále to však nedoporučujeme. Namísto toho doporučujeme použít **Správce vlastností** k vytvoření *vlastností* k uložení nastavení pro každý typ projektu, který chcete moci opakovaně používat nebo sdílet s ostatními. Seznamy vlastností také pomáhají zajistit, aby nedošlo k neúmyslné změně nastavení vlastností u dalších typů projektů. Seznamy vlastností jsou podrobněji [vytváření opakovaně použitelných vlastností konfigurací](#bkmkPropertySheets).

> [!IMPORTANT]
> **soubory .user a proč jsou problematické**
>
> Dřívější verze sady Visual Studio používaly globální tabulky vlastnosti, které měly příponu názvu souboru .user a byly umístěny ve \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ složky. Použití těchto souborů již nedoporučujeme, protože nastavují vlastnosti konfigurace projektu pro jednotlivé uživatele a počítače. Taková „globální“ nastavení mohou narušovat sestavení, zvláště když v sestavovacím počítači cílíte na více platforem. Pokud například máte projekt na platformě MFC i na platformě Windows Phone, vlastnosti v seznamu .user budou pro jeden z těchto projektů neplatné. Opakovaně použitelné seznamy vlastností jsou pružnější a odolnější.
>
> Přestože soubory .user se v sadě Visual Studio stále instalují a účastní se dědění vlastností, jsou ve výchozím nastavení prázdné. Osvědčeným postupem je odstranit odkazy na ně ve **Správce vlastností** zajistit, že projekty pracují nezávisle na jakémkoli uživatelské nastavení vázané na počítač to je důležité k zajištění správného chování v SCC (zdrojový kód ovládací prvek) prostředí.

Chcete-li zobrazit **Správce vlastností**, na panelu nabídek zvolte **zobrazení**, **ostatní Windows**, **Správce vlastností**.

Pokud máte běžnou, často používanou sadu vlastností, které chcete použít pro více projektů, můžete použít **Správce vlastností** k jejich zachycení do opakovaně použitelného *vlastností* soubor, který má přípona názvu souboru .props. Seznam (případně více seznamů) lze použít u nových projektů, takže nemusíte nastavovat jejich vlastnosti od začátku. Pro přístup k **Správce vlastností**, na panelu nabídek zvolte **zobrazení**, **Správce vlastností**.

![Správce vlastností nabídku](../ide/media/sharingnew.png "SharingNew")

Za každý uzel konfigurace najdete v článku uzly pro každý seznam vlastností, které platí pro tuto konfiguraci. Systém přidá seznam vlastností, které nastavte hodnoty podle možnosti zvolené v Průvodci vytvořením aplikace při vytváření projektu. Klikněte pravým tlačítkem na libovolný uzel a vyberte vlastnosti, které chcete zobrazit vlastnosti, které se vztahují k tomuto uzlu. Všechny seznamy vlastností jsou automaticky importovány do projektu "hlavní" vlastností (ms.cpp.props) a jsou vyhodnocovány v pořadí, ve kterém se zobrazují v Správce vlastností. Můžete je změnit pořadí vyhodnocování přesunout. Seznamy vlastností, které jsou vyhodnoceny později přepíšou hodnoty v tabulkách dříve vyhodnocen.

Pokud se rozhodnete **přidat nový seznam vlastností projektu** a vyberete například vlastností myprops.props, dialogové okno stránky vlastností zobrazí se. Všimněte si, že se týká seznamu vlastností MyProps. Jakékoli provedené změny se zapíší do tohoto seznamu, nikoli do souboru projektu (.vcxproj).

Pokud je stejná vlastnost nastavena přímo v souboru .vcxproj, vlastnosti v seznamu vlastností se přepíší.

Seznam vlastností můžete importovat tak často, jak potřebujete. Z jednoho seznamu vlastností může zdědit nastavení více projektů v řešení a projekt může obsahovat více seznamů. Samotný seznam vlastností může zdědit nastavení z jiného seznamu vlastností.

Můžete také vytvořit jeden seznam vlastností pro více konfigurací. K tomuto účelu vytvořte seznam vlastností pro každou konfiguraci, otevřete místní nabídku pro jeden z nich, zvolte **přidat existující seznam vlastností**a pak přidejte další listy. Pokud však používáte jeden společný seznam vlastností, nezapomeňte, že nastavená vlastnost se použije ve všech konfiguracích, ke kterým se seznam vztahuje, a že integrované vývojové prostředí neuvádí, které projekty nebo jiné seznamy vlastností z daného seznamu vlastností dědí.

V rozsáhlých řešeních, která budou obsahovat mnoho projektů, může být užitečné vytvořit seznam vlastností na úrovni řešení. Když přidáte projekt do řešení, použijte **Správce vlastností** do projektu přidat tento seznam vlastností. Pokud je to nutné na úrovni projektu, můžete přidat nový seznam vlastností, kterým se nastaví hodnoty specifické pro projekt.

> [!IMPORTANT]
> Soubor .props ve výchozím nastavení není součástí řízení zdroje, protože není vytvořen jako položka projektu. Pokud chcete soubor zahrnout do zdrojového kódu, můžete ho přidat ručně jako položku řešení.

#### <a name="to-create-a-property-sheet"></a>Vytvoření seznamu vlastností

1. V panelu nabídky zvolte **zobrazení**, **Správce vlastností**. **Správce vlastností** otevře.

2. Chcete-li definovat rozsah seznamu vlastností, vyberte položku, na kterou se vztahuje. Může se jednat o konkrétní konfiguraci nebo o jiný seznam vlastností. Otevřete místní nabídku pro tuto položku a klikněte na tlačítko **přidat nový seznam vlastností projektu**. Zadejte název a umístění seznamu.

3. V **Správce vlastností**, otevřete nový seznam vlastností a potom nastavte vlastnosti, které chcete zahrnout.

##  <a name="bkmkPropertyInheritance"></a> Dědičnost vlastnosti

Vlastnosti projektu jsou rozloženy do vrstev. Každá vrstva zdědí hodnoty předchozí vrstvy, ale zděděné hodnoty lze přepsat explicitním nastavením vlastností. Zde uvádíme základní strom dědičnosti:

1. Výchozí nastavení ze sady nástrojů MSBuild CPP (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, tj. soubor importovaný souborem .vcxproj.)

2. Seznamy vlastností

3. Soubor .vcxproj. (Může přepsat výchozí nastavení a nastavení seznamu vlastností.)

4. Metadata položek

> [!TIP]
> Na stránce vlastností je vlastnost v `bold` je definována v aktuálním kontextu. Vlastnost uvedená normálním písmem je zděděná.

Soubor projektu (.vcxproj) importuje v okamžiku sestavení další seznamy vlastností. Po importu všech seznamů vlastností je soubor projektu vyhodnocen a pro všechny hodnoty vlastností se použije jejich poslední definice. Někdy je užitečné zobrazit rozbalený soubor, ve kterém zjistíte, jak je hodnota dané vlastnosti zděděna. Rozbalenou verzi zobrazíte zadáním následujícího příkazu na příkazovém řádku Visual Studio. (Podle potřeby zaměňte zástupné symboly názvy souborů, které chcete použít.)

**Nástroj MSBuild /pp:** *temp* **.txt** *myapp* **.vcxproj**

Rozbalené soubory projektů mohou být velké a náročné na orientaci, pokud dobře neznáte nástroj MSBuild. Zde uvádíme základní strukturu souboru projektu:

1. Základní vlastnosti projektu, které nejsou vystaveny v integrovaném vývojovém prostředí

2. Import souboru Microsoft.cpp.default.props, který definuje některé základní vlastnosti nezávislé na sadách nástrojů

3. Vlastnosti globální konfigurace (vystavena jako **PlatformToolset** a **projektu** výchozí vlastnosti na **Obecná konfigurace** stránky. Tyto vlastnosti určují, která sada nástrojů a vnitřní seznamy vlastností se importují v souboru Microsoft.cpp.props v dalším kroku.

4. Import souboru Microsoft.cpp.props, který nastaví většinu výchozích hodnot projektu

5. Import všech seznamů vlastností, včetně souborů .user. Tyto seznamy vlastností mohou přepsat vše kromě **PlatformToolset** a **projektu** výchozí vlastnosti.

6. Zbývající vlastnosti konfigurace projektu Tyto hodnoty mohou přepsat nastavení provedená v seznamu vlastností.

7. Položky (soubory) spolu s příslušnými metadaty. Ty v pravidlech vyhodnocování MSBuild vždy dostanou prioritu, i když se vyskytují před dalšími vlastnostmi a importy.

Další informace najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).

## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>Přidání adresáře vkládaných souborů do sady výchozích adresářů

Přidáváte-li do projektu adresář vkládaných souborů, je důležité, abyste nepřepsali všechny výchozí adresáře. Správný způsob přidání adresáře je připojit novou cestu, například "C:\MyNewIncludeDir\"a potom připojit **$(IncludePath)** – makro do hodnoty vlastnosti.

## <a name="setting-environment-variables-for-a-build"></a>Nastavení proměnných prostředí pro sestavení

Kompilátor Visual C++ (cl.exe) rozpoznává určité proměnné prostředí, konkrétně LIB, LIBPATH, PATH a INCLUDE. Při sestavení s IDE vlastnosti, které jsou nastaveny [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md) stránku vlastností se používají k nastavení těchto proměnných prostředí. Pokud jsou hodnoty proměnných LIB, LIBPATH a INCLUDE již nastaveny, například pomocí příkazového řádku pro vývojáře, nahradí se hodnotami odpovídajících vlastností MSBuild. Sestavení poté připojí k proměnné PATH hodnotu vlastnosti spustitelných adresářů Adresáře VC++. Můžete nastavit proměnné prostředí definované uživatelem vytvořené uživatelem definované makro a potom zaškrtnete políčko s textem **nastavit toto makro jako proměnnou prostředí v prostředí pro sestavení**.

## <a name="setting-environment-variables-for-a-debugging-session"></a>Nastavení proměnných prostředí pro relaci ladicího programu

V levém podokně projektu **stránky vlastností** dialogového okna rozbalte **vlastnosti konfigurace** a pak vyberte **ladění**.

V pravém podokně upravte **prostředí** nebo **sloučit prostředí** nastavení projektu a klikněte na tlačítko **OK** tlačítko.

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>Úprava vlastností a cílů beze změny souboru projektu

Můžete přepsat vlastnosti projektu a cíle z příkazového řádku MSBuild beze změny souboru projektu. To je užitečné, pokud chcete použít některé vlastnosti dočasně nebo čas od času. Předpokládá základní znalost MSBuild. Další informace najdete v tématu [MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Můžete použít Editor XML v sadě Visual Studio nebo libovolného textového editoru vytvořte soubor PROPS nebo .targets. Nepoužívejte **Správce vlastností** v tomto scénáři protože přidá vlastnosti do souboru projektu.

*K přepsání vlastností projektu:*

1. Vytvořte soubor PROPS, která určuje vlastnosti, které chcete přepsat.

1. Z příkazového řádku: nastavte ForceImportBeforeCppTargets="C:\sources\my_props.props"

*Chcete-li přepsat cíle projektu:*

1. Vytvoření souboru .targets s jejich provádění nebo konkrétní cílový

2. Z příkazového řádku: nastavte ForceImportAfterCppTargets = "C:\sources\my_target.targets"

Můžete také nastavit jednu z možností příkazového řádku msbuild pomocí možnosti/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Přepsání vlastností a cílů tímto způsobem je ekvivalentní k přidání následující importy do všech souborů .vcxproj v řešení:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```

## <a name="see-also"></a>Viz také:

[Vytváření a spravování projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Struktura souborů .vcxproj a .props](vcxproj-file-structure.md)<br/>
[Soubory XML stránky vlastností](property-page-xml-files.md)<br/>
