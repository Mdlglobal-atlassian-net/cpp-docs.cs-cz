---
title: /JMC (ladění s možností Pouze můj kód)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 90fcad40b3322f8a8ae7ffc58875c2850f143138
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341009"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (ladění s možností Pouze můj kód)

Určuje podporu kompilátoru pro nativní ladění *pouze můj kód* v ladicím programu sady Visual Studio. Tato možnost podporuje uživatelská nastavení, která umožňují aplikaci Visual Studio krokovat se systémem, architekturou, knihovnou a dalšími neuživatelskými voláními a sbalovat tato volání v okně zásobníku volání. Možnost kompilátoru **/JMC** je k dispozici počínaje verzí Visual Studio 2017 verze 15,8.

## <a name="syntax"></a>Syntaxe

> **/JMC**\[ **-** ]

## <a name="remarks"></a>Poznámky

Nastavení sady Visual Studio [pouze můj kód](/visualstudio/debugger/just-my-code) určuje, zda ladicí program sady Visual Studio bude postupovat podle systému, architektury, knihovny a dalších volání bez uživatele. Možnost kompilátoru **/JMC** umožňuje podporu pro pouze můj kód ladění v nativním C++ kódu. Pokud je povolen **/JMC** , kompilátor vloží volání pomocné funkce `__CheckForDebuggerJustMyCode`v prologu funkce. Pomocná funkce poskytuje háky, které podporují Pouze můj kód kroků ladicího programu sady Visual Studio. Pokud chcete povolit pouze můj kód v ladicím programu sady Visual Studio, na panelu nabídek zvolte**Možnosti** **nástroje** > a pak nastavte možnost v části **ladění** > **Obecné** > **Povolit pouze můj kód**.

Možnost **/JMC** vyžaduje, aby váš kód propojuje knihovnu runtime jazyka C (CRT), která poskytuje `__CheckForDebuggerJustMyCode` pomocnou funkci. Pokud váš projekt neodkazuje na CRT, může se zobrazit chyba linkeru **linkerů LNK2019: nevyřešený externí symbol __CheckForDebuggerJustMyCode**. Tuto chybu můžete vyřešit tak, že buď propojíte s CRT, nebo zakážete možnost **/JMC** .

Ve výchozím nastavení je možnost kompilátoru **/JMC** vypnutá. V aplikaci Visual Studio 2017 verze 15,8 je však tato možnost povolena ve většině šablon projektů sady Visual Studio. Chcete-li explicitně zakázat tuto možnost, použijte možnost **/JMC-** na příkazovém řádku. V aplikaci Visual Studio otevřete dialogové okno stránky vlastností projektu a změňte vlastnost **Podpora pouze můj kódho ladění** na stránce vlastností  > konfigurace > **C/C++** **Obecné** na **Ne**.

Další informace naleznete v tématu [ C++ pouze můj kód](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) v tématu [určení toho, zda se má ladit pouze uživatelský kód pomocí pouze můj kód v aplikaci Visual Studio](/visualstudio/debugger/just-my-code)a Blogový příspěvek C++ týmu oznamuje, že se [v aplikaci Visual Studio C++ pouze můj kód krokování](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností **Konfigurace** > **C/C++**  > **Obecné** .

1. Upravte vlastnost **ladění Support pouze můj kód** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
