---
title: Obecná stránka vlastností (soubor)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: a9281a0ea02bd9b1fd529453cb9a67e54e4ddda7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168968"
---
# <a name="general-property-page-file"></a>Obecná stránka vlastností (soubor)

Toto téma se vztahuje na projekty Windows. Pro projekty jiné než Windows se podívejte [na C++ odkaz na stránku vlastností Linux](../../linux/prop-pages-linux.md).

Když kliknete pravým tlačítkem na **Průzkumník řešení**uzel souboru, otevře se stránka **Obecné** vlastnosti pod uzlem **Vlastnosti konfigurace** . Obsahuje následující vlastnosti:

- **Vyloučeno ze sestavení**

   Určuje, zda má být soubor v sestavení pro aktuální konfiguraci.

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Obsah** (platí jenom pro aplikace pro UWP) Určuje, jestli soubor obsahuje obsah, který se má zahrnout do balíčku aplikace.

- **Typ položky**

   **Typ položky** Určuje nástroj, který se použije ke zpracování souboru během procesu sestavení. [Soubory s příponou, jejichž rozšíření je známou v aplikaci Visual Studio](/visualstudio/extensibility/visual-cpp-project-extensibility?view=vs-2019#project-items) , mají v této vlastnosti výchozí hodnotu. Vlastní nástroj můžete zadat zde, pokud máte vlastní typ souboru nebo chcete přepsat výchozí nástroj pro známý typ souboru. Další informace najdete v tématu [určení nástrojů pro vlastní sestavení](../specifying-custom-build-tools.md) . Tuto stránku vlastností lze také použít k určení, že soubor není součástí procesu sestavení.

   Následující ilustrace znázorňuje stránku vlastností souboru *. cpp* . Výchozí **typ položky** pro tento typ souboru je **C/C++ Compiler** (*CL. exe*) a stránka vlastností zpřístupňuje různá nastavení kompilátoru, která lze použít pouze pro tento soubor.

   ![Obecná stránka vlastností pro položku projektu](media/file-general-item-type.png "Volby typu položky")

    Následující tabulka obsahuje seznam výchozích typů položek:

    |Přípona souboru|Typ položky|Výchozí nástroj|
    |-|-|-|
    |. appx|Definice aplikace XAML|[Balíček aplikace](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. HLSL,. CSO|Kompilátor HLSL|[fxc. exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/C++ hlavička|[Preprocesor C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |neuvedeno|Neúčastní se sestavení|neuvedeno|
    |. XML,. XSLT,. xsl|XML|[Editor XML](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resjson|Prostředek PRI (aplikace UWP)|[Předány MakePRI. exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Média (UWP)|[Balíček aplikace](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|Nástroj generátor dat XML|[Nástroj definice schématu XML (XSD. exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (vyžaduje úlohu rozhraní .NET. Není součástí MSVC.)|
    ||Nástroj manifest|[MT. exe](/windows/win32/sbscs/mt-exe)|
    |.rc|Prostředek|[Kompilátor prostředků Windows (RC. exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest|Manifest balíčku aplikace|[Balíček aplikace](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.obj|Objekt|[C/C++ Linker (Link. exe)](cl-invokes-the-linker.md)|
    |. ttf|Písma|neuvedeno|
    |.txt|Text|neuvedeno|
    |neuvedeno|Nástroj pro vlastní sestavení|Definované uživatelem|
    |neuvedeno|Kopírovat soubor|neuvedeno|
    |. packagelayout|Rozložení balíčku aplikace|[Balíček aplikace](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.resx|Spravovaný prostředek kompilátoru|[Resgen.exe (generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |. Natvis|C++Soubor vizualizace ladicího programu|[Systém Natvis](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |. jpg,. bmp,. ico atd.|Obrázek|Kompilátor prostředků založený na typu aplikace|
    |.cpp|C/C++ kompilátor|CL. exe|

   Chcete-li získat programový přístup k této vlastnosti, přečtěte si <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Informace o tom, jak získat přístup ke stránce **Obecné** vlastnosti pod uzlem **Vlastnosti konfigurace** , naleznete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Viz také

[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)
