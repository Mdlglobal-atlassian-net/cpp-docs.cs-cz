---
title: Stránka vlastností adresářů VC ++ | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs:
- C++
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3acaccff2e2764f4fd7f6f4815f5721f0ba845a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="vc-directories-property-page-windows"></a>Stránka adresářů VC ++ vlastnost (Windows)

Pomocí této stránky vlastností říct adresáře, které se má použít při sestavení projektu aktuálně vybrané sadě Visual Studio. Nastavení adresáře pro více projektů v řešení, použití vlastních vlastností způsobem popsaným v [vytváření konfigurace opakovaně použitelné vlastností](working-with-project-properties.md#bkmkPropertySheets).

Linux verzi této stránce, naleznete v části [adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md).   

Abyste měli přístup **adresáře VC ++** stránky vlastností:

1. Pokud **Průzkumníku řešení** okno není viditelný, pak v hlavní nabídce zvolte **zobrazení** > **Průzkumníku řešení**.
1. Klikněte pravým tlačítkem na uzel projektu (není nejvyšší úrovně řešení) a zvolte **vlastnosti**.
1. V levém podokně **stránky vlastností** dialogové okno, vyberte **vlastnosti konfigurace** > **adresáře VC ++**.  

Vlastnosti adresáře VC ++ se vztahují na projekt, ne uzlu nejvyšší úrovně řešení. Pokud se nezobrazí **adresáře VC ++** pod **vlastnosti konfigurace**, vyberte uzel projektu C++ v **Průzkumníku řešení** okno: 

![Vyberte uzel projektu](media/vcppdir.png "vyberte uzel projektu zobrazíte vlastnosti adresáře VC ++")

Všimněte si, že **adresáře VC ++** stránka vlastností pro různé platformy projekty vypadá jinak. Informace specifické pro projekty Linux C++ najdete v tématu [adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md). 
 
Pokud nejste obeznámeni s *projektu vlastnosti* v sadě Visual Studio, může pro vás užitečné první čtení [práce s vlastnostmi projektu](working-with-project-properties.md). 
 
Výchozí nastavení pro **adresáře VC ++** vlastnosti závisí na typu projektu. Pro stolní projekty obsahují umístění nástroje C++ pro konkrétní sada nástrojů platformy a umístění sady Windows SDK. Můžete změnit **sada nástrojů platformy** a **verze sady Windows SDK** na **vlastnosti konfigurace** > **Obecné** stránka. 

Chcete-li zobrazit hodnoty pro všechny adresáře:

1. Vyberte jednu z vlastností v **adresáře VC ++** stránky. Například vyberte **adresáře knihovny**.
1. Klikněte na tlačítko šipky dolů na konci tohoto pole hodnotu vlastnosti.
1. V rozevírací nabídce vyberte **upravit**.

![Upravit adresáře knihovny](media/vcppdir_libdir_edit.png "dialogové okno Upravit cesty knihoven")

Zobrazí dialogové okno takto: 

![Zobrazit adresáře knihovny](media/vcppdir_libdir.png "dialogové okno Přidat nebo odebrat cesty knihoven")

Chcete-li zobrazit aktuální adresáře pomocí tohoto dialogového okna. Ale pokud chcete změnit nebo přidat adresář, je lepší použít **Správce vlastností** k vytvoření seznamu vlastností, nebo úpravě vlastností výchozí uživatel. Další informace najdete v tématu [vytváření konfigurace opakovaně použitelné vlastností](working-with-project-properties.md#bkmkPropertySheets).

Jako v příkladu nahoře, řadu zděděné cesty jsou uvedeny jako makra.  Chcete-li zkontrolovat aktuální hodnota makra, zvolte **makra** tlačítko v pravém dolním rohu dialogu. Všimněte si, že mnoho makra závisí na konfiguraci typu. Makro v sestavení ladicí verze může vyhodnotit jiné cestě než stejné makro v sestavení pro vydání. 

Můžete hledat částečné nebo úplný odpovídá v textové pole. Následující obrázek znázorňuje všechny makra, které obsahují řetězec "WindowsSDK" a také ukazuje aktuální cestě, jehož výsledkem makro:

![Zobrazit hodnoty makro](media/vcppdir_libdir_macros.png "dialogové okno Upravit makra")

Poznámka: Naplnění seznamu během psaní. Nemáte stiskněte **Enter**.

Další informace o makra a proč byste měli používat místo pevně cest, kdykoli je to možné, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Seznam běžně používané makra najdete v tématu [běžné makra pro příkazy sestavení a vlastnosti](https://docs.microsoft.com/en-us/cpp/ide/common-macros-for-build-commands-and-properties).

Můžete definovat vlastní makra dvěma způsoby:
-   Nastavení proměnných prostředí v příkazovém řádku vývojáře. Všechny proměnné prostředí jsou považovány za MSBuild vlastnosti/makra.
-   Definice maker uživatele v souboru props. Další informace najdete v tématu [makra vlastností stránky](working-with-project-properties.md#bkmkPropertiesVersusMacros). 

Další informace najdete v tématu tyto příspěvky blogu: [adresáře VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [zděděné vlastnosti a seznam vlastností](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), a [Visual Studio 2010 C++ projektu průvodci upgradem](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Typy adresářů

Můžete zadat také další adresáře, a to následujícím způsobem.  
  
**Spustitelný soubor adresáře**<br/>
Adresáře, ve kterých se mají vyhledávat spustitelné soubory. Odpovídá **cesta** proměnné prostředí.

**Zahrnout adresáře**<br/>
Adresáře, ve kterých se mají vyhledávat vkládané soubory, na něž je odkazováno ze zdrojového kódu. Odpovídá **zahrnout** proměnné prostředí.

**Referenční dokumentace adresáře**<br/>
 Adresáře, ve kterém se má hledat sestavení a soubory modulu (metadata), které jsou odkazované ve zdrojovém kódu pomocí [#using](../preprocessor/hash-using-directive-cpp.md) – direktiva. Odpovídá **LIBPATH** proměnné prostředí.

**Adresáře knihovny**<br/>
Adresáře, ve kterých se mají vyhledávat soubory knihoven (.lib), včetně knihoven prostředí runtime. Odpovídá **LIB** proměnné prostředí. Toto nastavení se nevztahuje na soubory .obj; Chcete-li vytvořit odkaz na soubor .obj na **vlastnosti konfigurace** > **Linkeru** > **Obecné** stránka vlastností, vyberte  **Další závislosti knihovny** a pak zadejte relativní cesta k souboru. Další informace najdete v tématu [stránky vlastností Linkeru](../ide/linker-property-pages.md).

**Knihovna WinRT adresáře**<br/>
Adresáře k vyhledání WinRT soubory knihovny pro použití v aplikacích pro univerzální platformu Windows (UWP). 

**Zdrojové adresáře**<br/>
Adresáře, ve kterých se mají vyhledávat zdrojové soubory pro IntelliSense.

**Vyloučit adresáře**<br/>
Před každou kompilace Visual Studio dotazuje časové razítko všechny soubory k určení, zda všechny byla změněna od předchozí kompilace. Pokud váš projekt má velký stabilní knihovny, můžete potenciálně urychlit časy sestavení tak, že tyto adresáře vyloučíte z kontroly časové razítko.

## <a name="sharing-the-settings"></a>Sdílení nastavení

Vlastnosti projektu můžete sdílet s dalšími uživateli nebo napříč počítači. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).
