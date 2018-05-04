---
title: /Zc:threadSafeInit (vláken místní statické inicializace) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- threadSafeInit
- /Zc:threadSafeInit
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- threadSafeInit
- Thread-safe Local Static Initialization
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: a0fc4b34-2cf0-45a7-a642-b8afc4ca19f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 438ce5ba783f646e9c8e61d9b82999ea936532b4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="zcthreadsafeinit-thread-safe-local-static-initialization"></a>/Zc:threadSafeInit (vláken místní statické inicializace)

**/Zc:threadSafeInit** – možnost kompilátoru říká kompilátoru inicializovat statické místní (rozsah funkce) proměnné vláken způsobem, což eliminuje potřebu ruční synchronizace. Pouze inicializace je bezpečné pro přístup z více vláken. Používání a úpravy statické místní proměnné více podprocesů musí být stále ručně synchronizovány. Tato možnost je dostupná od ve Visual Studiu 2015. Ve výchozím nastavení povoluje Visual Studio tuto možnost.

## <a name="syntax"></a>Syntaxe

> **/Zc:threadSafeInit**[**-**]

## <a name="remarks"></a>Poznámky

V C ++ 11 standardní proměnné s rozsahem bloku se statickými nebo trvání uložení vlákno nutné nula inicializovat všechny ostatní inicializace probíhá. Inicializace nastane, když řízení prvním průchodu deklarace proměnné. Pokud je vyvolána výjimka při inicializaci, proměnné se považuje za Neinicializovaný a je znovu pokus o inicializaci na další ovládací prvek čas projdou deklaraci. Pokud ovládací prvek zadá deklaraci souběžně inicializace souběžné provádění bloky při dokončení inicializace. Chování není definována, pokud ovládací prvek znovu zadá rekurzivně deklarace během inicializace. Ve výchozím nastavení Visual Studio spouštění v sadě Visual Studio 2015 implementuje toto standardní chování. Toto chování může být explicitně určen nastavením **/Zc:threadSafeInit** – možnost kompilátoru.

**/Zc:threadSafeInit** – možnost kompilátoru ve výchozím nastavení zapnutý. [/ Projektovou-](permissive-standards-conformance.md) možnost nemá vliv na **/Zc:threadSafeInit**.

Inicializace statické lokální proměnné vláken závisí na kódu implementované v knihovně Universal C Runtime (UCRT). Vyhnout se závislost na UCRT, nebo chcete zachovat chování není bezpečná pro přístup z více vláken inicializace verze sady Visual Studio před Visual Studio 2015, použít **/Zc:threadSafeInit-** možnost. Pokud víte, že tento vláken není povinný, tuto možnost použijte ke generování mírně nižší a rychlejší kódu kolem statické místní deklarace.

Úložiště thread-local (TLS) statické lokální proměnné vláken interně použít k efektivní provádění když statických již byl inicializován. Implementace této funkce spoléhá na podporu funkce operačního systému Windows ve Windows Vista a novějších operačních systémech. Windows XP, Windows Server 2003 a starších operačních systémů nemají tato podpora, takže Nezískávat zlepšení výkonu. Tyto operační systémy také mít nižší limit počtu TLS oddíly, které je možné načíst. Překročení TLS části limit může způsobit selhání. Pokud se jedná o problém v kódu, zejména v kódu, který se musí spustit na starší operační systémy, používat **/Zc:threadSafeInit-** zakázat kód inicializace bezpečné pro přístup z více vláken.

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Z **konfigurace** rozevírací nabídce, zvolte **všechny konfigurace**.

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **příkazového řádku** stránku vlastností.

1. Změnit **další možnosti** vlastnost, aby zahrnovala **/Zc:threadSafeInit** nebo **/Zc:threadSafeInit-** a potom zvolte **OK**.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (shoda)](../../build/reference/zc-conformance.md)<br/>
