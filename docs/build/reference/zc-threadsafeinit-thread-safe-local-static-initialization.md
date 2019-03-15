---
title: '/ Zc: threadsafeinit (bezpečná pro vlákno lokální statická inicializace)'
ms.date: 03/14/2018
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
ms.openlocfilehash: 92a1bfa5ec3bab2814397d51e35e617b7666c706
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808336"
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/ Zc: threadsafeinit (bezpečná pro vlákno lokální statická inicializace)

**/Zc: threadsafeinit** – možnost kompilátoru instruuje kompilátor, aby inicializovat proměnné (rozsah funkce) statické místní způsobem bezpečným pro vlákno, takže odpadá potřeba ruční synchronizace. Je jenom inicializace bezpečná pro vlákno. Použití a změny statických lokálních proměnných ve víc vláknech je pořád nutná ruční synchronizace. Tato možnost je k dispozici od verze Visual Studio 2015. Ve výchozím nastavení sada Visual Studio umožňuje tuto možnost.

## <a name="syntax"></a>Syntaxe

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Poznámky

V C ++ 11 standard proměnné s rozsahem bloku se statickými nebo dobou trvání úložiště vlákna musí být nula inicializován před další inicializace probíhá. Inicializace nastane, pokud ovládací prvek prvním průchodu deklarace proměnné. Pokud dojde k výjimce během inicializace proměnné se považuje za neinicializované a je znovu pokus o inicializaci další čas řízení se předá prostřednictvím deklarace. Pokud ovládacího prvku zadá deklarace současně inicializace, bloky souběžné spouštění během inicializace je dokončena. Chování není definováno, pokud ovládací prvek znovu zadá rekurzivně deklarace během inicializace. Ve výchozím nastavení Visual Studio, počínaje verzí Visual Studio 2015 implementuje toto chování standard. Toto chování může být explicitně zadán tak, že nastavíte **/Zc: threadsafeinit** – možnost kompilátoru.

**/Zc: threadsafeinit** – možnost kompilátoru je ve výchozím. [/ Permissive-](permissive-standards-conformance.md) nemá vliv na možnost **/Zc: threadsafeinit**.

Bezpečná pro vlákno inicializace statických lokálních proměnných závisí na kódu implementované v knihovně Universal C Runtime (UCRT). Vyhnete se tak závislosti na UCRT nebo zachování chování vláknově bezpečné inicializace verzí sady Visual Studio před Visual Studio 2015, použijte **/Zc: threadsafeinit** možnost. Pokud víte, že zabezpečení tohoto vlákna se nevyžaduje, použijte tuto možnost Generovat kód o něco menší a rychlejší kolem statické místní deklarace.

Vláknově bezpečné statické lokální proměnné úložiště thread local (TLS) se používají interně k poskytování účinného provádění, když statické již byl inicializován. Implementace této funkce závisí na podporu funkce operačního systému Windows v systémech Windows Vista a novějších operačních systémech. Windows XP, Windows Server 2003 a starších operačních systémech není nutné tuto podporu, proto nelze získat výhody efektivitu. Tyto operační systémy také mít dolní mez počtu oddílů TLS, které je možné načíst. Překročení limitu TLS limit části může způsobit selhání. Pokud tento problém v kódu, zejména v kódu, který musí být spuštěn ve starších operačních systémech, je použít **/Zc: threadsafeinit** zakázat kód inicializace bezpečná pro vlákno.

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Z **konfigurace** rozevírací nabídku, vyberte **všechny konfigurace**.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Upravit **další možnosti** vlastnost, aby zahrnovala **/Zc: threadsafeinit** nebo **/Zc: threadsafeinit** a klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (shoda)](zc-conformance.md)<br/>
