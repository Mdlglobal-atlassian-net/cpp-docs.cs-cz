---
title: Stránka vlastností adresářů VC ++ | Dokumentace Microsoftu
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
ms.openlocfilehash: 82aaa2dc43177963b9b38c398e74aaa0ffff11dd
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821215"
---
# <a name="vc-directories-property-page-windows"></a>VC ++ Directories Property Page (Windows)

Pomocí této stránky vlastností říct adresáře, které se má použít při vytváření aktuálně vybraného projektu sady Visual Studio. Nastavení adresáře pro více projektů v řešení, použijte seznam vlastních vlastností, jak je popsáno v [vytváření opakovaně použitelných vlastností konfigurací](working-with-project-properties.md#bkmkPropertySheets).

Verzi Linuxu na této stránce, najdete v části [adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md).

Pro přístup **adresáře VC ++** stránky vlastností:

1. Pokud **Průzkumníka řešení** okno se nezobrazuje, pak v hlavní nabídce zvolte **zobrazení** > **Průzkumníku řešení**.
1. Klikněte pravým tlačítkem na uzel projektu (nikoli řešení nejvyšší úrovně) a zvolte **vlastnosti**.
1. V levém podokně **stránky vlastností** dialogu **vlastnosti konfigurace** > **adresáře VC ++**.

Adresáře VC ++ vlastnosti se vztahují k projektu, ne uzel nejvyšší úrovně řešení. Pokud nevidíte **adresáře VC ++** pod **vlastnosti konfigurace**, vyberte uzel projektu C++ ve **Průzkumníka řešení** okno:

![Vyberte uzel projektu](media/vcppdir.png "vyberte uzel projektu můžete zobrazit vlastnosti adresáře VC ++")

Všimněte si, že **adresáře VC ++** stránku vlastností pro multiplatformní projekty vypadá jinak. Informace specifické pro projekty C++ pro Linux najdete v tématu [adresáře VC ++ (Linux C++)](../linux/prop-pages/directories-linux.md).

Pokud nejste obeznámeni s *vlastnosti projektu* v sadě Visual Studio, možná pro vás bude užitečné první čtení [práce s vlastnostmi projektu](working-with-project-properties.md).

Výchozí nastavení pro **adresáře VC ++** vlastnosti závisí na typu projektu. Pro desktopové projekty obsahují umístění nástroje C++ pro konkrétní sadu nástrojů platformy a umístění sady Windows SDK. Můžete změnit **sada nástrojů platformy** a **verze sady Windows SDK** na **vlastnosti konfigurace** > **Obecné** stránka.

Chcete-li zobrazit hodnoty pro všechny adresáře:

1. Vyberte jednu z vlastností v **adresáře VC ++** stránky. Například zvolte **adresáře knihoven**.
1. Klikněte na tlačítko šipky dolů na konci pole hodnoty vlastnosti.
1. V rozevírací nabídce vyberte **upravit**.

![Upravit adresáře knihoven](media/vcppdir_libdir_edit.png "dialogové okno Úprava cesty knihoven")

Zobrazí dialogové okno takto:

![Zobrazit adresáře knihoven](media/vcppdir_libdir.png "dialogové okno pro přidání nebo odebrání cesty knihoven")

Použijte toto dialogové okno k zobrazení aktuálního adresáře. Pokud chcete změnit nebo přidat adresáře, je ale vhodnější použít **Správce vlastností** můžete vytvořit seznam vlastností nebo upravit výchozí uživatelský seznam vlastností. Další informace najdete v tématu [vytváření opakovaně použitelných vlastností konfigurací](working-with-project-properties.md#bkmkPropertySheets).

Jak uvádíme výš, řadu zděděné cesty jsou uvedeny jako makra.  Chcete-li zkontrolovat aktuální hodnotu makra, zvolte **makra** tlačítko v pravém dolním rohu dialogového okna. Všimněte si, že mnoho makra závisí na konfiguraci typu. Makra v sestavení pro ladění může být vyhodnocen na jinou cestu než stejný – makro v sestavení pro vydání.

Můžete hledat částečné nebo úplné shody do textového pole. Následující obrázek znázorňuje všechna makra, které obsahují řetězec "WindowsSDK" a také zobrazuje aktuální cestu, která se vyhodnotí jako makra:

![Zobrazit hodnoty makra](media/vcppdir_libdir_macros.png "dialogové okno Upravit makra")

Poznámka: Naplnění seznamu při psaní. Není stiskněte **Enter**.

Další informace o makra a proč byste měli používat namísto pevně zakódovaných cest, kdykoli je to možné, naleznete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md#bkmkPropertiesVersusMacros).

Seznam běžně používaných maker naleznete v tématu [běžné Macros for Build Commands and Properties](https://docs.microsoft.com/cpp/ide/common-macros-for-build-commands-and-properties).

Můžete definovat vlastní makra dvěma způsoby:

- Nastavení proměnných prostředí v příkazovém řádku pro vývojáře. Všechny proměnné prostředí jsou považovány za MSBuild vlastnosti a makra.

- V souboru .props definujte uživatelská makra. Další informace najdete v tématu [makra stránky vlastností](working-with-project-properties.md#bkmkPropertiesVersusMacros).

Další informace najdete v tématu příspěvky na blogu: [adresáře VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [zděděné vlastnosti a seznamy vlastností](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), a [Visual Studio 2010 C++ Průvodce upgradem projektu](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).

## <a name="directory-types"></a>Typy adresářů

Můžete zadat také další adresáře, a to následujícím způsobem.

**Adresáře spustitelných souborů**<br/>
Adresáře, ve kterých se mají vyhledávat spustitelné soubory. Odpovídá **cesta** proměnné prostředí.

**Adresáře souborů k zahrnutí**<br/>
Adresáře, ve kterých se mají vyhledávat vkládané soubory, na něž je odkazováno ze zdrojového kódu. Odpovídá **zahrnout** proměnné prostředí.

**Adresáře odkazů**<br/>
Adresáře, ve kterých chcete hledat sestavení a souborech modulů (metadata), které jsou odkazované ze zdrojového kódu pomocí [#using](../preprocessor/hash-using-directive-cpp.md) směrnice. Odpovídá **LIBPATH** proměnné prostředí.

**Adresáře knihoven**<br/>
Adresáře, ve kterých se mají vyhledávat soubory knihoven (.lib), včetně knihoven prostředí runtime. Odpovídá **LIB** proměnné prostředí. Toto nastavení se nevztahuje na soubory. obj. pro propojení souboru .obj, na **vlastnosti konfigurace** > **Linkeru** > **Obecné** stránky vlastností, vyberte  **Další závislosti knihoven** a potom zadejte relativní cestu k souboru. Další informace najdete v tématu [stránky vlastností Linkeru](../ide/linker-property-pages.md).

**Adresáře knihoven WinRT**<br/>
Adresáře pro vyhledávání souborů knihoven WinRT pro použití v aplikacích pro univerzální platformu Windows (UPW).

**Adresáře zdrojových souborů**<br/>
Adresáře, ve kterých se mají vyhledávat zdrojové soubory pro IntelliSense.

**Vyloučené adresáře**<br/>
Visual Studio před každou kompilace dotazuje časové razítko u všech souborů k určení, zda všechny změněné od předchozího sestavení. Pokud váš projekt obsahuje velké stabilní knihovny, můžete potenciálně urychlit dobu sestavení podle těchto adresáře vyloučíte z kontroly časové razítko.

## <a name="sharing-the-settings"></a>Sdílení nastavení

Vlastnosti projektu můžete sdílet s dalšími uživateli nebo napříč počítači. Další informace najdete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).
