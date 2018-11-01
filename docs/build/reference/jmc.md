---
title: / JMC (ladění pouze můj kód)
ms.date: 08/20/2018
f1_keywords:
- /JMC
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: a81292b590d96ef93446f9bb59af305c7eda2ef9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516854"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC (ladění pouze můj kód)

Určuje podporu kompilátoru pro nativní *pouze můj kód* ladění v ladicím programu sady Visual Studio. Tato možnost podporuje uživatelská nastavení, které umožní sadě Visual Studio Krokovat přes systém, rozhraní, knihovny a další neuživatelská volání a sbalí tato volání do okna zásobník volání. **/JMC** – možnost kompilátoru je k dispozici od verze Visual Studio 2017 verze 15.8.

## <a name="syntax"></a>Syntaxe

> **/ JMC**\[**-**]

## <a name="remarks"></a>Poznámky

Visual Studio [pouze můj kód](/visualstudio/debugger/just-my-code) nastavení určuje, zda ladicí program sady Visual Studio kroky systému a rozhraní, knihovny a další neuživatelská volání. **/JMC** – možnost kompilátoru umožňuje podporu pro ladění pouze můj kód v nativním kódu C++. Když **/JMC** je povoleno, kompilátor vloží volání pomocné funkce, `__CheckForDebuggerJustMyCode`, v prologu funkce. Pomocná funkce poskytuje zachytávání, které podporují operace kroku pouze můj kód ladicího programu sady Visual Studio. Chcete-li povolit volbu pouze vlastní kód v ladicím programu sady Visual Studio, na panelu nabídek zvolte **nástroje** > **možnosti**a pak nastavte možnost v **ladění**  >  **Obecné** > **povolit volbu pouze vlastní kód**.

**/JMC** možnost vyžaduje, že váš kód odkazuje na C Runtime Library (CRT), která poskytuje `__CheckForDebuggerJustMyCode` pomocnou funkci. Pokud projekt neobsahuje odkazy na CRT, může se zobrazit chyba linkeru **LNK2019: nevyřešené externí symbol __CheckForDebuggerJustMyCode**. Chcete-li vyřešit tuto chybu, propojit k CRT, nebo zakázat **/JMC** možnost.

Ve výchozím nastavení **/JMC** – možnost kompilátoru je vypnuté. Ale spuštění v sadě Visual Studio 2017 verze 15.8 Tato možnost je povolená většina šablony projektů Visual Studio. Chcete-li explicitně zakázat tuto možnost, použijte **/JMC-** možnost na příkazovém řádku. V sadě Visual Studio, otevřete dialogové okno stránky vlastností projektu a změňte **podporu pouze můj kód ladění** vlastnost **vlastnosti konfigurace** > **C/C++**  >  **Obecné** na stránce vlastností **ne**.

Další informace najdete v tématu [pouze můj kód C++](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) v [určit, jestli se má ladit jenom uživatelský kód, pomocí funkce pouze můj kód v sadě Visual Studio](/visualstudio/debugger/just-my-code)a v příspěvku blogu týmu Visual C++ [oznamujeme C++ pouze můj kód Krokování v sadě Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **Obecné** stránku vlastností.

1. Upravit **podporu pouze můj kód ladění** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
