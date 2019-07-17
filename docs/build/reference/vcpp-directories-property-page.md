---
title: Stránka vlastností adresářů VC++
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
ms.openlocfilehash: 9b005a89156db48615ec6ea8dfc4f07a7414fc3b
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299778"
---
# <a name="vc-directories-property-page-windows"></a>Stránka vlastností adresářů VC + + (Windows)

Pomocí této stránky vlastností můžete aplikaci Visual Studio sdělit, které adresáře se mají použít při vytváření aktuálně vybraného projektu. Chcete-li nastavit adresáře pro více projektů v řešení, použijte vlastní seznam vlastností, jak je popsáno v tématu [sdílení nebo C++ opětovné použití nastavení projektu sady Visual Studio](../create-reusable-property-configurations.md).

Verzi této stránky pro Linux najdete v tématu [adresáře VC + + (Linux C++)](../../linux/prop-pages/directories-linux.md).

Přístup ke stránce vlastností **adresářů VC + +** :

1. Pokud okno **Průzkumník řešení** není viditelné, v hlavní nabídce zvolte možnost **Zobrazit** > **Průzkumník řešení**.
1. Klikněte pravým tlačítkem myši na uzel projektu (ne na řešení nejvyšší úrovně) a vyberte příkaz **vlastnosti**.
1. V levém podokně dialogového okna **stránky vlastností** vyberte možnost **vlastnosti** > konfigurace**adresáře VC + +** .

Vlastnosti adresářů VC + + se vztahují na projekt, nikoli na uzel řešení na nejvyšší úrovni. Pokud se v části **Vlastnosti konfigurace**nezobrazí C++ **adresáře VC + +** , vyberte uzel projektu v okně **Průzkumník řešení** :

![Vybrat uzel projektu](../media/vcppdir.png "Vyberte uzel projektu pro zobrazení vlastností adresářů VC + +") .

Všimněte si, že stránka vlastností **adresářů VC + +** pro projekty pro různé platformy vypadá jinak. Informace specifické pro projekty Linux C++ naleznete v tématu [adresáře VC + + (Linux C++)](../../linux/prop-pages/directories-linux.md).

Pokud nejste obeznámeni s *vlastnostmi projektu* v sadě Visual Studio, může být užitečné nejprve načíst [nastavení kompilátoru a C++ vlastností sestavení v sadě Visual Studio](../working-with-project-properties.md).

Výchozí nastavení pro vlastnosti **adresářů VC + +** závisí na typu projektu. Pro desktopové projekty zahrnují umístění C++ nástrojů pro konkrétní sadu nástrojů platformy a umístění Windows SDK. Na stránce**Obecné** **vlastnosti** > konfigurace můžete změnit **sadu nástrojů platformy** a **verzi Windows SDK** .

Chcete-li zobrazit hodnoty pro některý z adresářů:

1. Vyberte jednu z vlastností na stránce **adresáře VC + +** . Například vyberte **adresáře knihoven**.
1. Klikněte na tlačítko se šipkou dolů na konci pole hodnota vlastnosti.
1. V rozevírací nabídce vyberte možnost **Upravit**.

![Upravit adresáře knihoven](../media/vcppdir_libdir_edit.png "Dialog pro úpravu cest knihovny")

Teď se zobrazí dialogové okno, které vypadá takto:

![Zobrazit adresáře knihoven](../media/vcppdir_libdir.png "Dialogové okno pro přidání nebo odebrání cest knihovny")

Pomocí tohoto dialogového okna můžete zobrazit aktuální adresáře. Pokud ale chcete změnit nebo přidat adresář, je vhodnější použít **Správce vlastností** k vytvoření seznamu vlastností nebo k úpravě výchozího uživatelského seznamu vlastností. Další informace najdete v tématu [sdílení nebo opětovné použití nastavení C++ projektu sady Visual Studio](../create-reusable-property-configurations.md).

Jak vidíte výše, mnoho z děděných cest se předává jako makra.  Chcete-li prostudovat aktuální hodnotu makra, klikněte na tlačítko **makra** v pravém dolním rohu dialogového okna. Všimněte si, že mnoho maker závisí na typu konfigurace. Makro v sestavení ladění může být vyhodnoceno na jinou cestu než stejné makro v sestavení pro vydání.

V poli pro úpravy můžete vyhledat částečné nebo úplné shody. Následující ilustrace znázorňuje všechna makra, která obsahují řetězec "WindowsSDK" a také zobrazuje aktuální cestu, na kterou se makro vyhodnocuje:

![Zobrazit hodnoty maker](../media/vcppdir_libdir_macros.png "Dialog pro úpravu maker")

Poznámka: Seznam se naplní při psaní. Nestiskněte klávesu **ENTER**.

Další informace o makrech a proč byste je měli použít místo pevně zakódovaných cest, pokud je to možné, najdete v tématu [Nastavení vlastností kompilátoru a sestavení v C++ sadě Visual Studio](../working-with-project-properties.md).

Seznam běžně používaných maker naleznete v tématu [společná makra pro příkazy a vlastnosti sestavení](common-macros-for-build-commands-and-properties.md).

Vlastní makra můžete definovat dvěma způsoby:

- Nastavte proměnné prostředí na příkazovém řádku pro vývojáře. Všechny proměnné prostředí jsou považovány za vlastnosti nebo makra nástroje MSBuild.

- Definujte uživatelská makra v souboru. props. Další informace najdete v tématu [makra stránky vlastností](../working-with-project-properties.md).

Další informace najdete v těchto blogových příspěvcích: [Adresáře VC + +](https://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [zděděné vlastnosti, seznamy vlastností](https://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx)a [Průvodce upgradem C++ projektu sady Visual Studio 2010](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/).

## <a name="directory-types"></a>Typy adresářů

Můžete zadat také další adresáře, a to následujícím způsobem.

**Spustitelné adresáře**<br/>
Adresáře, ve kterých se mají vyhledávat spustitelné soubory. Odpovídá proměnné prostředí **path** .

**Adresáře souborů k zahrnutí**<br/>
Adresáře, ve kterých se mají vyhledávat vkládané soubory, na něž je odkazováno ze zdrojového kódu. Odpovídá proměnné prostředí **include** .

**Adresáře odkazů**<br/>
Adresáře, ve kterých se mají vyhledávat soubory sestavení a modulu (metadata), na které odkazuje zdrojový kód pomocí direktivy [#using](../../preprocessor/hash-using-directive-cpp.md) . Odpovídá proměnné prostředí **LIBPATH** .

**Adresáře knihoven**<br/>
Adresáře, ve kterých se mají vyhledávat soubory knihoven (.lib), včetně knihoven prostředí runtime. Odpovídá proměnné prostředí **lib** . Toto nastavení se nevztahuje na soubory. obj; Chcete-li vytvořit odkaz na soubor. obj, na stránce **vlastnosti** > konfigurace**Obecné** vlastnosti**linkeru** > vyberte **Další závislosti knihoven** a pak zadejte relativní cestu k souboru. Další informace najdete v tématu [stránky vlastností linkeru](linker-property-pages.md).

**Adresáře knihovny WinRT**<br/>
Adresáře, ve kterých se mají hledat soubory knihovny WinRT pro použití v aplikacích Univerzální platforma Windows (UWP)

**Zdrojové adresáře**<br/>
Adresáře, ve kterých se mají vyhledávat zdrojové soubory pro IntelliSense.

**Vyloučit adresáře**<br/>
Před každou kompilací aplikace Visual Studio dotazuje časové razítko pro všechny soubory, aby bylo možné určit, zda byly od předchozí kompilace změněny. Pokud má váš projekt velké stabilní knihovny, můžete potenciálně zrychlit sestavení tím, že tyto adresáře vyjmete z kontroly časového razítka.

## <a name="sharing-the-settings"></a>Sdílení nastavení

Vlastnosti projektu můžete sdílet s dalšími uživateli nebo napříč počítači. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).
