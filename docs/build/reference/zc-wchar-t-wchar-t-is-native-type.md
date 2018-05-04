---
title: '/ Zc: wchar_t (wchar_t je nativní typ) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 061aa4a70412a0b51450470e690bea5633b764ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t je nativní typ)

Analyzovat `wchar_t` jako předdefinovaný typ podle C++ standard.

## <a name="syntax"></a>Syntaxe

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Poznámky

Pokud **/Zc:** je, `wchar_t` je klíčové slovo pro předdefinovaný integrální typ v kódu kompilovány jako C++. Pokud **/Zc:wchar_t-** (se znaménkem minus) je zadán, nebo v kódu kompilována jako C, `wchar_t` není typu předdefinované. Místo toho `wchar_t` je definován jako `typedef` pro `unsigned short` v kanonickém tvaru záhlaví stddef.h. (Microsoft implementace definuje ho v jiné záhlaví, která je zahrnutá ve stddef.h a dalších hlavičky standardních.)

Nedoporučujeme **/Zc:wchar_t-** protože C++ standard vyžaduje, aby `wchar_t` být předdefinovaný typ. Pomocí `typedef` verze může způsobit problémy přenositelnost. Pokud jste upgrade z předchozích verzí aplikace Visual C++ a dojde k chybě kompilátoru [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) protože kód se bude snažit implicitně převést `wchar_t` k `unsigned short`, doporučujeme vám, že změníte kód, který řešení chyby, místo toho nastavení **/Zc:wchar_t-**.

**/Zc:** možnost je ve výchozím v kompilaci C++ a je ignorován v kompilaci C. [/ Projektovou-](permissive-standards-conformance.md) možnost nemá vliv na **/Zc:**.

Microsoft implementuje `wchar_t` jako hodnotu dva bajtů bez znaménka. Se mapuje na typ nativní specifické pro společnost Microsoft `__wchar_t`. Další informace o `wchar_t`, najdete v části [rozsahy datového typu](../../cpp/data-type-ranges.md) a [základní typy](../../cpp/fundamental-types-cpp.md).

Pokud zadat nový kód, který má pro spolupráci s starší kód, který stále používá `typedef` verzi `wchar_t`, můžete zadat přetížení pro obě `unsigned short` a `__wchar_t` variace `wchar_t`tak, aby váš kód může být propojený s kód kompilovat s **/Zc:** nebo kompilovat bez kódu. Jinak, budete muset zadejte dva různé sestavení knihovny, jednu s a druhou bez **/Zc:** povolena. Také v tomto případě doporučujeme sestavit starší kód pomocí stejného kompilátoru, jaký používáte ke kompilaci nového kódu. Nikdy nekombinujte binární soubory zkompilované různými kompilátory.

Když **/Zc:** není zadaný,  **\_WCHAR\_T\_DEFINOVANÁ** a  **\_NATIVNÍ\_WCHAR\_T\_DEFINOVANÁ** značky jsou definovány. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).

Pokud váš kód používá globální funkce kompilátoru modelu COM, protože **/Zc:** je teď na ve výchozím nastavení, doporučujeme, abyste změnili explicitní odkazy na comsupp.lib (buď z [komentář – Direktiva pragma](../../preprocessor/comment-c-cpp.md) nebo na příkazový řádek) comsuppw.lib nebo comsuppwd.lib. (Pokud je nutné kompilovat s **/Zc:wchar_t-**, použijte comsupp.lib.) Při vložení hlavičkového souboru comdef.h je správná knihovna určena automaticky. Informace týkající se podpory kompilátoru modelu COM, najdete v článku [podpory kompilátoru modelu COM](../../cpp/compiler-com-support.md).

`wchar_t` Předdefinovaný typ není podporován při kompilaci kódu jazyka C. Další informace o problémech shoda s Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **jazyk** stránky.

1. Změnit **wchar_t považovat za předdefinovaný typ** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>Viz také

[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
