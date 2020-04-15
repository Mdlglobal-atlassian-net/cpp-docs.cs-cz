---
title: /QIfist (Potlačit _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336099"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (Potlačit _ftol)

Zastaralé Potlačí volání pomocné funkce, `_ftol` když je vyžadován převod z typu s plovoucí desetinnou tácek na integrální typ.

## <a name="syntax"></a>Syntaxe

```
/QIfist
```

## <a name="remarks"></a>Poznámky

> [!NOTE]
> **/QIfist** je k dispozici pouze v kompilátoru cílení x86; tato možnost kompilátoru není k dispozici v kompilátorech zaměřených na x64 neboARM.

Kromě převodu z typu s plovoucí desetinnou `_ftol` desetinnou na integrální typ funkce zajišťuje, že režim zaokrouhlení jednotky s plovoucí desetinnou desetinnou tázkou směřuje k nule (zkrácení) nastavením bitů 10 a 11 řídicího slova. To zaručuje, že převod z typu s plovoucí desetinnou čárkou na integrální typ probíhá podle popisu standardu ANSI C (zlomková část čísla je zahozena). Při použití **/QIfist**tato záruka již neplatí. Režim zaokrouhlení bude jeden ze čtyř, jak je popsáno v referenčních příručkách společnosti Intel:

- Zaokrouhlit směrem k nejbližší (sudé číslo, pokud je ve stejné vzdálenosti)

- Zaokrouhlit směrem k zápornému nekonečnu

- Zaokrouhlit směrem k kladnému nekonečnu

- Zaokrouhlit směrem k nule

Funkci [_control87, _controlfp _control87_2 \_](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run-Time můžete použít k úpravě chování zaokrouhlení FPU. Výchozí režim zaokrouhlení FPU je "Zaoblení směrem k nejbližšímu". Použití **/QIfist** může zlepšit výkon vaší aplikace, ale ne bez rizika. Měli byste důkladně otestovat části kódu, které jsou citlivé na režimy zaokrouhlení před spoléháním na kód vytvořený pomocí **/QIfist** v produkčním prostředí.

[/arch (x86)](arch-x86.md) a **/QIfist** nelze použít na stejném compiland.

> [!NOTE]
> **/QIfist** není ve výchozím nastavení v platnosti, protože bity zaokrouhlení také ovlivňují plovoucí bod na zaokrouhlení s plovoucí desetinnou tázkou (ke kterému dochází po každém výpočtu), takže když nastavíte příznaky pro zaokrouhlování ve stylu C (směrem k nule), výpočty s plovoucí desetinnou desetinnou úta se mohou lišit. **/QIfist** by neměl být používán, pokud váš kód závisí na očekávané morálce zkrácení zlomkové části čísla s plovoucí desetinnou čárkou. Pokud si nejste jisti, nepoužívejte **/QIfist**.

Možnost **/QIfist** je zastaralé počínaje Visual Studio 2005. Kompilátor provedl významné zlepšení rychlosti převodu plovoucí na int. Seznam zastaralých možností kompilátoru naleznete **v tématu Zastaralé a odebrané možnosti kompilátoru** v [možnostech kompilátoru uvedených podle kategorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na složku **C/C++.**

1. Klepněte na stránku vlastností **příkazového řádku.**

1. Do pole **Další možnosti** zadejte možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[/Q – možnosti (operace nízké úrovně)](q-options-low-level-operations.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
