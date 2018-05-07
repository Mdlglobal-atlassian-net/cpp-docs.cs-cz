---
title: Práce s vlastnostmi projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 3c33a18ff0d492ef3a870a342c9d8ff292007748
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-project-properties"></a>Práce s vlastnostmi projektu
V prostředí IDE, veškeré informace, které je potřebné k vytvoření projektu je k dispozici jako *vlastnosti*. Tyto informace zahrnují název aplikace, rozšíření (například knihovny DLL, LIB, EXE), – možnosti kompilátoru, možnosti linkeru, nastavení ladicího programu, vlastní kroky sestavení a mnoho dalších položek. Obvykle použijete, *stránky vlastností* ( **projektu &#124; vlastnosti**) můžete zobrazit a upravit tyto vlastnosti. 
  
 Když vytvoříte projekt, systém přiřadí hodnoty pro různé vlastnosti. Výchozí hodnoty lišit v závislosti na druhu projektu a jaké možnosti, můžete vybrat v Průvodci vytvořením aplikace. Například projektu knihovny ATL má vlastnosti týkající se soubory MIDL, ale tyto chybí v základní konzolovou aplikaci. Výchozí vlastnosti jsou uvedeny v podokně Obecné stránky vlastností:  
  
 ![Visual C&#43; &#43; projektu výchozí](../ide/media/visual-c---project-defaults.png "výchozí nastavení projektu Visual C++")  
  
 Některé vlastnosti, jako je například název aplikace, se vztahují na všechny varianty sestavení, bez ohledu na cílové platformy nebo zda je ladění nebo verze sestavení. Ale většinu vlastností jsou závislá na konfiguraci. Je to proto, že má kompilátor vědět, jaké konkrétní platformu, která se bude program spouštět v a jaké konkrétní kompilátoru možnosti má použít k vygenerování správný kód. Proto když nastavíte vlastnost, je důležité věnovat pozornost které konfigurace a nová hodnota by se měly používat pro platformu. Měli použít pouze na sestavení pro ladění Win32 nebo také používat na ladění ARM a ladění x64? Například **optimalizace** , ve výchozím nastavení, je nastavena na **maximalizovat rychlost (/ O2)** v rámci konfigurace verze, ale je zakázán v konfiguraci ladění.  
  
 Stránky vlastností jsou navržené tak, že vždycky uvidíte a v případě potřeby upravit, které konfigurace a platformy hodnotu vlastnosti by se měly používat k. Následující obrázek znázorňuje do seznamu polí v horní části stránky vlastností se konfigurace a platformy informace. Když **optimalizace** zde nastavena vlastnost, bude se vztahovat jenom na sestavení pro ladění Win32, která se dělá jako aktivní konfigurace jako red šipek.  
  
 ![Visual C&#43; &#43; stránky vlastností zobrazuje aktivní konfigurace](../ide/media/visual-c---property-pages-showing-active-configuration.png "aktivní konfigurace zobrazuje Visual C++ – stránky vlastností")  
  
 Následující obrázek znázorňuje stejné stránce vlastností projektu, ale konfigurace se změnil na verzi. Všimněte si jinou hodnotu pro vlastnost optimalizace. Všimněte si také, že aktivní konfigurace je stále ladění. Můžete nastavit vlastnosti pro všechny konfigurace zde; nemusí to být aktivní.  
  
 ![Visual C&#43; &#43; stránky vlastností zobrazuje verze konfigurace](../ide/media/visual-c---property-pages-showing-release-config.png "konfigurace verzí znázorňující Visual C++ – stránky vlastností")  
  
 Systém projektu, samotné je založen na MSBuild, který definuje formáty souborů a pravidla pro vytváření projektů jakéhokoli druhu. MSBuild spravuje většinu složitosti budova více konfigurace a platformy, ale budete muset chvíli pochopit, jak funguje. To je obzvláště důležité, pokud chcete definovat vlastní konfigurace nebo vytvořit opakovaně použitelný sady vlastností, které můžete sdílet a importovat do více projektů.  
  
 Vlastnosti projektu ukládají přímo v souboru projektu (*.vcxproj) nebo v jiné soubory .xml nebo props importuje soubor projektu a který dodávat výchozí hodnoty. Jak je uvedeno výše, může stejnou vlastnost pro stejnou konfiguraci přiřadit jinou hodnotu v různých souborů. Při sestavování projektu nástroje MSBuild modul vyhodnocuje souboru projektu a všech importovaných souborů v dobře definovaný pořadí (popsaný níže). Jako vyhodnotí každý soubor, všechny hodnoty vlastností, které jsou definované v tomto souboru přepíše existující hodnoty. Všechny hodnoty, které nebyly zadány dědí ze souborů, které byly vyhodnoceny dříve. Proto když nastavíte vlastnost s použitím stránek vlastností, je také důležité věnovat pozornost kde nastavíte. Pokud nastavíte vlastnost "X" v souboru props, ale vlastnost je nastavena na "Y" v souboru projektu, se sestavení projektu s vlastnost nastavená na "Y". Pokud stejný vlastnost nastavena na "Z" na Položka projektu, jako je soubor sada, bude používat modul MSBuild hodnotu "Z". Další informace najdete v tématu [dědičnost vlastnosti](#bkmkPropertyInheritance) dále v tomto článku.  
  
## <a name="build-configurations"></a>Konfigurace sestavení  
 Konfigurace je právě libovolné skupině vlastnosti, které mají název. Visual Studio poskytuje konfigurace Debug a Release a každý nastaví různé vlastnosti pro sestavení ladicí verze nebo verze sestavení. Můžete použít **nástroje Configuration Manager** se definovat vlastní konfigurace pohodlný způsob pro vlastnosti skupiny pro konkrétní příchuť sestavení. Správce vlastností se používá pro pokročilé práce s vlastnostmi, ale jeho protože pomáhá vizualizovat konfigurace vlastností zavedeme sem. Přístup k z **zobrazení &#124; Správce vlastností** nebo **zobrazení &#124; ostatní okna &#124; Správce vlastností** v závislosti na nastavení. V projektu má uzlů pro jednotlivé páry konfigurace/platformy. V každém tyto uzly jsou uzly pro seznamy vlastností (soubory props), které nastavit některé vlastnosti specifické pro danou konfiguraci.  
  
 ![Správce vlastností](../ide/media/property-manager.png "Správce vlastností")  
  
 Pokud přejděte do podokna obecné na stránkách vlastností (viz výše uvedeném obrázku) a nastavte vlastnost znaková sada pro "Není nastavena" místo "Použití Unicode" a klikněte na **OK**, Správce vlastností zobrazí žádné **Podpora kódování Unicode** vlastností pro aktuální konfiguraci, ale bude stále existuje pro ostatní konfigurace.  
  
 Další informace o Správci vlastností a seznamech vlastností, najdete v tématu [vytváření opakovaně použitelných vlastnost konfigurace](#bkmkPropertySheets) dále v tomto článku.  
  
> [!TIP]
>  Soubor .uživatel je starší verze funkce a doporučujeme odstranit abychom zachovali vlastnosti správně seskupené podle konfigurace/platformy.  
  
## <a name="target-platforms"></a>Cílové platformy  
 *Cílová platforma* odkazuje na typ zařízení a/nebo operační systém, který se spustí spustitelný soubor na. Můžete vytvořit projekt pro více než jedné platformě. K dispozici cílových platforem pro projekty C++ závisí na druhu projektu; zahrnout, ale nejsou omezeny na Win32, x64, ARM, Android a iOS.     **X86** Cílová platforma, která můžete vidět v **nástroje Configuration Manager** je stejný jako **Win32** nativní projektech C++. Win32 znamená 32bitový systém Windows a **x64** znamená 64bitová verze Windows. Další informace o těchto dvou platforem najdete v tématu [spuštění 32bitové aplikace](https://msdn.microsoft.com/library/windows/desktop/aa384249\(v=vs.85\).aspx).  
  
 **Libovolný procesor** cílové platformy hodnotu, která můžete vidět v **nástroje Configuration Manager** nemá žádný vliv na nativní projekty C++; je relevantní pro C + +/ CLI a dalších .NET typy projektů. Další informace najdete v tématu [/CLRIMAGETYPE (zadat typ z obrázku CLR)](../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
## <a name="property-pages"></a>Stránky vlastností  
 Jak jsme uvedli dříve, systém projektu Visual C++ je založen na [MSBuild](/visualstudio/msbuild/msbuild-properties) a hodnoty jsou uloženy v souboru projektu XML, výchozí soubory props a .targets. Pro Visual Studio 2015, tyto soubory jsou umístěny v **\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140**. Pro Visual Studio 2017, tyto soubory jsou umístěny v  **\\Program Files (x86)\\Microsoft Visual Studio\\2017\\_edition_\\Common7\\ IDE\\VC\\VCTargets**, kde _edice_ je nainstalované verze sady Visual Studio. Vlastnosti jsou uloženy i v všechny vlastní props soubory, které můžete přidat do vlastní projektu. Důrazně doporučujeme že není upravit tyto soubory ručně a místo toho použít stránek vlastností v prostředí IDE upravit všechny vlastnosti, především těch, které jsou součástí dědičnosti, pokud mají velmi dobrou znalost nástroje MSBuild.  
  
 Následující obrázek znázorňuje stránky vlastností projektu jazyka Visual C++. V levém podokně klikněte **adresáře VC ++ *** pravidlo* je vybrána, a v pravém podokně zobrazí vlastnosti, které jsou přidružené daného pravidla. `$(...)` Hodnoty, se nazývají bohužel *makra*. Jedná se o *není* makra jazyka C/C++, ale jednoduše kompilaci konstanty. Makra, jsou popsané v [makra vlastností stránky](#bkmkPropertiesVersusMacros) později v tomto článku.)  
  
 ![Stránky vlastností projektu](../ide/media/project_property_pages_vc.png "Project_Property_Pages_VC")  
  
> [!WARNING]
>  **Společných vlastností** konfigurace v dřívějších verzích sady Visual Studio se odebraly. Přidat odkaz na projekt, můžete nyní používat **přidat odkaz na** dialogové okno stejným způsobem jako u spravované jazyky. V tématu [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project).  
  
#### <a name="to-set-a-property-for-a-project"></a>Nastavení vlastnosti projektu  
  
1.  Pro většinu scénářů můžete nastavit vlastnosti na úrovni projektu bez vytvoření vlastních vlastností. V hlavní nabídce zvolte **projektu &#124; vlastnosti**, nebo klikněte pravým tlačítkem na uzel projektu v **Průzkumníku řešení** a zvolte **vlastnosti**.  
  
2.  Použití **konfigurace** a **platformy** seznamu polí v horní části dialogových oken k určení, které vlastnost skupiny by se měly používat vaše změny. V mnoha případech **všechny platformy** a **všechny konfigurace** jsou správná volba. Nastavení vlastností pro některé konfigurace vícenásobný výběr je v **Správce vlastností**a pak otevřete místní nabídku a vyberte **vlastnosti**.  
  
 **Stránky vlastností** dialogové okno zobrazí pouze stránky vlastností, které se vztahují k aktuálnímu projektu. Pokud například projekt nemá soubor .idl, stránka s vlastnostmi MIDL se nezobrazí.  
  
 Když zvýrazníte vlastnost na stránce vlastnosti, můžete stisknout **F1** přejít na referenční téma pro další informace o odpovídající přepínače kompilátoru nebo linkeru.  
  
 Další informace o každé stránce vlastnost najdete v těchto tématech:  
  
-   [Obecná stránka vlastností (projekt)](../ide/general-property-page-project.md)  
  
-   [Obecná stránka vlastností (soubor)](../ide/general-property-page-file.md)  
  
-   [Stránky vlastností příkazového řádku](../ide/command-line-property-pages.md)  
  
-   [Nastavení projektu pro konfiguraci ladění jazyka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration)  
  
-   [NMake – stránka vlastností](../ide/nmake-property-page.md)  
  
-   [Stránky vlastností linkeru](../ide/linker-property-pages.md)  
  
-   [Stránky vlastností prostředků](../ide/resources-property-pages.md)  
  
-   [MIDL – stránky vlastností](../ide/midl-property-pages.md)  
  
-   [Stránka vlastností webových odkazů](../ide/web-references-property-page.md)  
  
-   [Stránka vlastností nástroje Generátor dat XML](../ide/xml-data-generator-tool-property-page.md)  
  
## <a name="to-quickly-browse-and-search-all-properties"></a>Chcete-li rychle procházet a vyhledejte všechny vlastnosti  
 **Všechny možnosti** stránka vlastností (v části **vlastnosti konfigurace &#124; C/C++** uzel v **stránky vlastností** dialogové okno) poskytuje rychlý způsob, jak procházet a vyhledejte vlastnosti, které jsou dostupné v aktuálním kontextu. Obsahuje speciální vyhledávací pole s jednoduchou syntaxí umožňující filtrovat výsledky:  
  
 Bez předpony:  
 Prohledávat pouze názvy vlastností (podřetězec bez rozlišení velkých a malých písmen)  
  
 '/' nebo '-':  
 Prohledávat pouze přepínače kompilátoru (předpona nerozlišující velká a malá písmena)  
  
 v:  
 Prohledávat pouze hodnoty (podřetězec bez rozlišení velkých a malých písmen)  
  
##  <a name="bkmkPropertiesVersusMacros"></a> Makra stránky vlastností  
 A *makro* kompilaci konstanta, která může označovat hodnotu, která je definována v sadě Visual Studio nebo MSBuild systému, nebo hodnotu definovanou uživatelem. Použijete-li makra namísto pevně definovaných hodnot, jako jsou například cesty k adresářům, můžete snadněji sdílet nastavení vlastností mezi počítači a mezi verzemi sady Visual Studio a lépe tak zajistit, aby se nastavení projektu řádně zapojilo do dědičnosti vlastností. Můžete si prohlédněte hodnoty všech dostupných maker Editor vlastností.  
  
### <a name="predefined-macros"></a>Předdefinovaná makra  
 globální makra  
 Platí pro všechny položky v konfiguraci projektu. Má syntaxi `$(name)`. Je například globální makro `$(VCInstallDir)`, která ukládá do kořenového adresáře instalace Visual Studia. Globální makro odpovídá `PropertyGroup` v nástroji MSBuild.  
  
 makra položky  
 Má syntaxi `%(name)`. Makro aplikace položky pro soubor, se vztahuje pouze na tento soubor – můžete použít například `%(AdditionalIncludeDirectories)` zadat zahrnuté adresáře, které se vztahují pouze na konkrétní soubor. Tento druh položky makro odpovídá `ItemGroup` metadata v nástroji MSBuild. Pokud se používá v kontextu konfigurace projektu, platí makro položky pro všechny soubory určitého typu. Například C/C++ **Definice preprocesoru** vlastnosti konfigurace může trvat `%(PreprocessorDefinitions)` makra položky, které se vztahují na všechny soubory sada v projektu. Tento druh položky makro odpovídá `ItemDefinitionGroup` metadata v nástroji MSBuild. Další informace najdete v tématu [definice položek](/visualstudio/msbuild/item-definitions).  
  
### <a name="user-defined-macros"></a>Uživatelská makra  
 Můžete vytvořit *uživatelská makra* používat jako proměnné v sestavení projektu. Můžete například vytvořit uživatelem definované makro poskytující hodnotu pro vlastní krok sestavení nebo pro vlastní nástroj sestavení. Uživatelem definované makro je pár název/hodnota. V souboru projektu, použijte **$(***název***)** zápis pro přístup k hodnotě.  
  
 Uživatelem definované makro je uloženo v seznamu vlastností. Pokud váš projekt již neobsahuje seznamu vlastností, můžete vytvořit pomocí následujících kroků v části [vytváření konfigurace opakovaně použitelné vlastností](#bkmkPropertySheets).  
  
##### <a name="to-create-a-user-defined-macro"></a>Vytvoření uživatelem definovaného makra  
  
1.  V **Správce vlastností** okno (na řádku nabídek zvolte **zobrazení**, **Správce vlastností**), otevřete místní nabídku pro seznam vlastností (název končí v .uživatel) a potom vyberte Vlastnosti. **Stránky vlastností** otevře dialogové okno pro tento list vlastností.  
  
2.  V levém podokně dialogového okna, vyberte **uživatele makra**. V pravém podokně vyberte **přidat makro** tlačítko Otevřít **přidat uživatelské makro** dialogové okno.  
  
3.  V dialogovém okně zadejte název a hodnotu makra. Volitelně vyberte **Nastaví makro jako proměnné prostředí v prostředí sestavení** zaškrtávací políčko.  
  
## <a name="property-editor"></a>Editor vlastností  
 Editor vlastností můžete použít ke změně některých vlastností řetězce a k výběru maker jako hodnot. Editor vlastností otevřete tak, že vyberete vlastnost na stránce vlastností a pak kliknete na šipku dolů na pravé straně. Pokud v rozevíracím seznamu jsou uvedeny  **\<Upravit >**, pak můžete zobrazit vlastnosti Editor pro tuto vlastnost.  
  
 ![Vlastnost&#95;Editor&#95;rozevírací](../ide/media/property_editor_dropdown.png "Property_Editor_Dropdown")  
  
 V editoru vlastností můžete **makra** tlačítko Zobrazit dostupné makra a jejich aktuální hodnoty. Následující obrázek znázorňuje vlastnost Editor pro **další adresáře Include** vlastnost po **makra** tlačítko jste vybrali. Když **zděděné z nadřazené nebo produktu project výchozí hodnoty** políčko a přidejte novou hodnotu, je připojen k žádné hodnoty, které jsou aktuálně zděděna. Pokud zaškrtnutí políčka zrušíte, nahradí nová hodnota zděděné hodnoty. Ve většině případů ponechte políčko zaškrtnuté.  
  
 ![Vlastnost editor, Visual C&#43;&#43;](../ide/media/propertyeditorvc.png "PropertyEditorVC")  
  
##  <a name="bkmkPropertySheets"></a> Vytváření opakovaně použitelných vlastnosti konfigurace  
 Je možné nastavit rovněž „globální“ vlastnosti podle jednotlivých uživatelů nebo počítačů, nadále to však nedoporučujeme. Místo toho doporučujeme používat **Správce vlastností** k vytvoření *vlastností* k ukládání nastavení pro jednotlivé typy projekt, který chcete mít možnost opakovaně použít nebo sdílet s ostatními. Seznamy vlastností také pomáhají zajistit, aby nedošlo k neúmyslné změně nastavení vlastností u dalších typů projektů. Seznam vlastností jsou popsány podrobněji [vytváření konfigurace opakovaně použitelné vlastností](#bkmkPropertySheets).  
  
> [!IMPORTANT]
>  **soubory .uživatel a proč jsou problematické**  
>   
>  Použít globální vlastností, které měl příponu názvu souboru .uživatel a se nacházely v minulých verzí sady Visual Studio \<userprofile > \AppData\Local\Microsoft\MSBuild\v4.0\ složky. Použití těchto souborů již nedoporučujeme, protože nastavují vlastnosti konfigurace projektu pro jednotlivé uživatele a počítače. Taková „globální“ nastavení mohou narušovat sestavení, zvláště když v sestavovacím počítači cílíte na více platforem. Pokud například máte projekt na platformě MFC i na platformě Windows Phone, vlastnosti v seznamu .user budou pro jeden z těchto projektů neplatné. Opakovaně použitelné seznamy vlastností jsou pružnější a odolnější.  
>   
>  Přestože soubory .user se v sadě Visual Studio stále instalují a účastní se dědění vlastností, jsou ve výchozím nastavení prázdné. Osvědčeným postupem je odstraňte odkaz na nich **Správce vlastností** zajistit, že projekty fungovat nezávisle na všechny uživatele, nastavení podle počítače to je důležité zajistit správné chování v SCC (zdrojový kód prostředí řízení).  
  
 Chcete-li zobrazit **Správce vlastností**, na řádku nabídek zvolte **zobrazení**, **ostatní okna**, **Správce vlastností**.  
  
 Pokud máte sadu běžných, často používané vlastnosti, které chcete použít pro více projektů, můžete použít **Správce vlastností** k jejich zachycení v opakovaně použitelného *vlastností* souboru, který má podle konvence přípona názvu souboru props. Seznam (případně více seznamů) lze použít u nových projektů, takže nemusíte nastavovat jejich vlastnosti od začátku. Pro přístup k **Správce vlastností**, na řádku nabídek zvolte **zobrazení**, **Správce vlastností**.  
  
 ![Správce vlastností místní nabídky](../ide/media/sharingnew.png "SharingNew")  
  
 V každém uzlu Konfigurace zobrazí uzlů pro každý vlastností, které platí pro danou konfiguraci. Systém přidá vlastností, které nastavte hodnoty na základě možností, které zvolíte v Průvodci vytvořením aplikace při vytváření projektu. Klikněte pravým tlačítkem na libovolný uzel a vyberte možnost Vlastnosti zobrazíte vlastnosti, které se vztahují k tomuto uzlu. Všechny vlastností automaticky importují do projektu "hlavní" vlastností (ms.cpp.props) a jsou vyhodnocovány v pořadí, ve kterém se objeví ve Správci vlastností. Je změna pořadí hodnocení se můžete přesunout. Seznamy vlastností, které se vyhodnocují později přepíše hodnoty v listech nástroje dříve vyhodnotit.  
  
 Pokud se rozhodnete **přidat nový seznam vlastností projektu** a pak vyberte položku, například MyProps.props vlastností, dialogové okno Vlastnosti stránky se zobrazí. Všimněte si, že se týká seznamu vlastností MyProps. Jakékoli provedené změny se zapíší do tohoto seznamu, nikoli do souboru projektu (.vcxproj).  
  
 Pokud je stejná vlastnost nastavena přímo v souboru .vcxproj, vlastnosti v seznamu vlastností se přepíší.  
  
 Seznam vlastností můžete importovat tak často, jak potřebujete. Z jednoho seznamu vlastností může zdědit nastavení více projektů v řešení a projekt může obsahovat více seznamů. Samotný seznam vlastností může zdědit nastavení z jiného seznamu vlastností.  
  
 Můžete také vytvořit jeden seznam vlastností pro více konfigurací. K tomuto účelu vytvořte seznam vlastností pro každou konfiguraci, otevřete místní nabídky pro jeden z nich, zvolte **přidat existující seznam vlastností**a poté přidejte ostatní listy. Pokud však používáte jeden společný seznam vlastností, nezapomeňte, že nastavená vlastnost se použije ve všech konfiguracích, ke kterým se seznam vztahuje, a že integrované vývojové prostředí neuvádí, které projekty nebo jiné seznamy vlastností z daného seznamu vlastností dědí.  
  
 V rozsáhlých řešeních, která budou obsahovat mnoho projektů, může být užitečné vytvořit seznam vlastností na úrovni řešení. Pokud do řešení přidat k projektu, použijte **Správce vlastností** přidání tohoto seznamu vlastností do projektu. Pokud je to nutné na úrovni projektu, můžete přidat nový seznam vlastností, kterým se nastaví hodnoty specifické pro projekt.  
  
> [!IMPORTANT]
>  Soubor .props ve výchozím nastavení není součástí řízení zdroje, protože není vytvořen jako položka projektu. Pokud chcete soubor zahrnout do zdrojového kódu, můžete ho přidat ručně jako položku řešení.  
  
#### <a name="to-create-a-property-sheet"></a>Vytvoření seznamu vlastností  
  
1.  Na řádku nabídek zvolte **zobrazení**, **Správce vlastností**. **Správce vlastností** otevře.  
  
2.  Chcete-li definovat rozsah seznamu vlastností, vyberte položku, na kterou se vztahuje. Může se jednat o konkrétní konfiguraci nebo o jiný seznam vlastností. Otevřete místní nabídku pro tuto položku a potom zvolte **přidat nový seznam vlastností projektu**. Zadejte název a umístění seznamu.  
  
3.  V **Správce vlastností**, otevřete nové okno vlastností a nastavte vlastnosti, které chcete zahrnout.  
  
##  <a name="bkmkPropertyInheritance"></a> Dědičnost vlastnosti  
 Vlastnosti projektu jsou rozloženy do vrstev. Každá vrstva zdědí hodnoty předchozí vrstvy, ale zděděné hodnoty lze přepsat explicitním nastavením vlastností. Zde uvádíme základní strom dědičnosti:  
  
1.  Výchozí nastavení ze sady nástrojů MSBuild CPP (..\Program Files\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props, tj. soubor importovaný souborem .vcxproj.)  
  
2.  Seznamy vlastností  
  
3.  Soubor .vcxproj. (Může přepsat výchozí nastavení a nastavení seznamu vlastností.)  
  
4.  Metadata položek  
  
> [!TIP]
>  Na stránce vlastností, vlastnost v `bold` je definována v aktuálním kontextu. Vlastnost uvedená normálním písmem je zděděná.  
  
 Soubor projektu (.vcxproj) importuje v okamžiku sestavení další seznamy vlastností. Po importu všech seznamů vlastností je soubor projektu vyhodnocen a pro všechny hodnoty vlastností se použije jejich poslední definice. Někdy je užitečné zobrazit rozbalený soubor, ve kterém zjistíte, jak je hodnota dané vlastnosti zděděna. Rozbalenou verzi zobrazíte zadáním následujícího příkazu na příkazovém řádku Visual Studio. (Podle potřeby zaměňte zástupné symboly názvy souborů, které chcete použít.)  
  
 **MSBuild /pp:** *temp* **.txt** *Moje aplikace* **VCXPROJ**  
  
 Rozbalené soubory projektů mohou být velké a náročné na orientaci, pokud dobře neznáte nástroj MSBuild. Zde uvádíme základní strukturu souboru projektu:  
  
1.  Základní vlastnosti projektu, které nejsou vystaveny v integrovaném vývojovém prostředí  
  
2.  Import souboru Microsoft.cpp.default.props, který definuje některé základní vlastnosti nezávislé na sadách nástrojů  
  
3.  Globální vlastnosti konfigurace (zveřejněné jako **PlatformToolset** a **projektu** výchozí vlastnosti na **obecné konfigurace** stránky. Tyto vlastnosti určují, která sada nástrojů a vnitřní seznamy vlastností se importují v souboru Microsoft.cpp.props v dalším kroku.  
  
4.  Import souboru Microsoft.cpp.props, který nastaví většinu výchozích hodnot projektu  
  
5.  Import všech seznamů vlastností, včetně souborů .user. Tyto seznamy vlastností můžete přepsat všechno kromě **PlatformToolset** a **projektu** výchozí vlastnosti.  
  
6.  Zbývající vlastnosti konfigurace projektu Tyto hodnoty mohou přepsat nastavení provedená v seznamu vlastností.  
  
7.  Položky (soubory) spolu s příslušnými metadaty. Ty v pravidlech vyhodnocování MSBuild vždy dostanou prioritu, i když se vyskytují před dalšími vlastnostmi a importy.  
  
 Další informace najdete v tématu [vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties).  
  
## <a name="adding-an-include-directory-to-the-set-of-default-directories"></a>Přidání adresáře vkládaných souborů do sady výchozích adresářů  
 Přidáváte-li do projektu adresář vkládaných souborů, je důležité, abyste nepřepsali všechny výchozí adresáře. Je správný způsob, jak přidat adresář připojit novou cestu, například "C:\MyNewIncludeDir\"a potom k připojení **$(IncludePath)** makro hodnota vlastnosti.  
  
## <a name="setting-environment-variables-for-a-build"></a>Nastavení proměnných prostředí pro sestavení  
 Kompilátor Visual C++ (cl.exe) rozpoznává určité proměnné prostředí, konkrétně LIB, LIBPATH, PATH a INCLUDE. Při vytváření pomocí rozhraní IDE, vlastnosti, které jsou nastavené [stránka vlastností adresářů VC ++](../ide/vcpp-directories-property-page.md) stránka vlastností slouží k nastavení těchto proměnných prostředí. Pokud jsou hodnoty proměnných LIB, LIBPATH a INCLUDE již nastaveny, například pomocí příkazového řádku pro vývojáře, nahradí se hodnotami odpovídajících vlastností MSBuild. Sestavení poté připojí k proměnné PATH hodnotu vlastnosti spustitelných adresářů Adresáře VC++. Můžete nastavit proměnnou uživatelské prostředí pomocí vytvořené uživatelské makro a potom zaškrtnutím políčka, která uvádí, že **Nastaví makro jako proměnné prostředí v prostředí sestavení**.  
  
## <a name="setting-environment-variables-for-a-debugging-session"></a>Nastavení proměnných prostředí pro relaci ladicího programu  
 V levém podokně projektu **stránky vlastností** dialogové okno, rozbalte seznam **vlastnosti konfigurace** a pak vyberte **ladění**. 
  
 V pravém podokně, upravte **prostředí** nebo **sloučení prostředí** nastavení projektu a klikněte **OK** tlačítko.  

## <a name="modifying-properties-and-targets-without-changing-the-project-file"></a>Úprava vlastností a cíle beze změny souboru projektu
Vlastnosti projektu a cíle z příkazového řádku nástroje MSBuild můžete přepsat beze změny souboru projektu. To je užitečné, pokud chcete použít některé vlastnosti dočasně nebo občas. Předpokládá znalost MSBuild. Další informace najdete v tématu [MSBUild](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Editor XML v sadě Visual Studio nebo libovolného textového editoru, slouží k vytvoření souboru props nebo .targets. Nepoužívejte **Správce vlastností** v tomto scénáři protože přidává vlastnosti k souboru projektu.

*Přepsání vlastností projektu:*
- Vytvořte soubor PROPS, který určuje vlastnosti, které chcete přepsat. 
- Z příkazového řádku: nastavte ForceImportBeforeCppTargets="C:\sources\my_props.props"
 
*Chcete-li přepsat cíle projektu:*
1) Vytvoření souboru .targets s jejich provádění nebo konkrétní cílový
2) Z příkazového řádku: nastavte ForceImportAfterCppTargets = "C:\sources\my_target.targets"
 
Můžete také nastavit jednu z možností na příkazovém řádku msbuild pomocí možnosti/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props" 
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets" 
```  

Přepsání vlastností a cíle tímto způsobem je ekvivalentní k přidávání následující importy ke všem souborům VCXPROJ v řešení:

```cmd 
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```  

## <a name="see-also"></a>Viz také  
 [Vytváření a správa projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md) [VCXPROJ a props souboru struktura](vcxproj-file-structure.md) [souborů XML stránky vlastností](property-page-xml-files.md)