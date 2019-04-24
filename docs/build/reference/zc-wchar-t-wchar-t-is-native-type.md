---
title: /Zc:wchar_t (wchar_t je nativní typ)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: b2563ba0ae2a07bc9f9d81128745ed4b9651fb6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315635"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

Analyzovat `wchar_t` jako předdefinovaný typ podle standardu jazyka C++.

## <a name="syntax"></a>Syntaxe

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc: wchar_t** zapnutý, `wchar_t` je klíčové slovo pro vestavěný celočíselný typ v kódu zkompilovaném jako C++. Pokud **/Zc:wchar_t-** (se znaménkem minus) je zadán, nebo v kódu zkompilovat jako C, `wchar_t` není vestavěný typ. Místo toho `wchar_t` je definován jako `typedef` pro `unsigned short` v kanonické hlavička stddef.h. (Microsoft implementace ji definuje v jiné záhlaví, který je součástí stddef.h a další standardní záhlaví.)

Nedoporučujeme **/Zc:wchar_t-** vzhledem k tomu, C++ standard vyžaduje, aby `wchar_t` předdefinovaným typem. Použití `typedef` verze může způsobit problémy s přenositelností. Pokud upgradujete ze starší verze Visual C++ a dojde k chybě kompilátoru [upozornění C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) protože kód se snaží implicitně převést `wchar_t` k `unsigned short`, doporučujeme vám, že změníte kód, který opravit chybu, Namísto nastavení **/Zc:wchar_t-**.

**/Zc: wchar_t** možnost je ve výchozím v C++ kompilace a je ignorován v jazyce C kompilacích. [/ Permissive-](permissive-standards-conformance.md) nemá vliv na možnost **/Zc: wchar_t**.

Microsoft implementuje `wchar_t` jako hodnota bez znaménka dva bajtu. Mapuje se na nativní typ specifické pro společnost Microsoft `__wchar_t`. Další informace o `wchar_t`, naleznete v tématu [rozsahy datového typu](../../cpp/data-type-ranges.md) a [základní typy](../../cpp/fundamental-types-cpp.md).

Pokud píšete nový kód, který má pro spolupráci s starší kód, který používá stále `typedef` verzi `wchar_t`, můžete poskytovat přetížení pro obě `unsigned short` a `__wchar_t` variace `wchar_t`tak, aby váš kód může být propojený s kód zkompilovaný s **/Zc: wchar_t** nebo kompilaci bez kódu. V opačném případě budete muset poskytnout dvě různá sestavení knihovny – jednu s a bez **/Zc: wchar_t** povolena. Také v tomto případě doporučujeme sestavit starší kód pomocí stejného kompilátoru, jaký používáte ke kompilaci nového kódu. Nikdy nekombinujte binární soubory zkompilované různými kompilátory.

Když **/Zc: wchar_t** není zadána,  **\_WCHAR\_T\_definované** a  **\_NATIVNÍ\_WCHAR\_T\_definované** jsou definovány symboly. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).

Pokud váš kód používá globální funkce kompilátoru modelu COM, protože **/Zc: wchar_t** je teď na ve výchozím nastavení, doporučujeme vám, že změníte explicitní odkazy na knihovnu comsupp.lib (buď z [comment – Direktiva pragma](../../preprocessor/comment-c-cpp.md) nebo příkazový řádek) comsuppw.lib nebo comsuppwd.lib. (Pokud je nutné kompilovat s **/Zc:wchar_t-**, použijte knihovnu comsupp.lib.) Při vložení hlavičkového souboru comdef.h je správná knihovna určena automaticky. Informace o podpoře modelu COM kompilátoru najdete v tématu [Compiler COM Support](../../cpp/compiler-com-support.md).

`wchar_t` Předdefinovaný typ není podporován při kompilaci kódu jazyka C. Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránky.

1. Upravit **považovat typ wchar_t za zabudovaný typ** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)<br/>
