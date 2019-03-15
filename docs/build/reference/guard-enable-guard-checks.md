---
title: /GUARD (povolení kontroly ochrany)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: e48921e57977cc7a1ca6a580fed78a6a2a960a02
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818411"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (povolení kontroly ochrany)

Určuje podporu toku provádění kontrol v spustitelné bitové kopie.

## <a name="syntax"></a>Syntaxe

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Poznámky

Pokud/Guard: CF je zadán, linker změní záhlaví .dll nebo .exe označíte, podpora pro kontroly za běhu Guard toku řízení (CFG). Linker také přidá požadovaný ovládací prvek tok cílové adresy data do záhlaví. / Guard: CF je ve výchozím nastavení zakázána. To může být explicitně zakázat pomocí /GUARD:NO. Aby byla účinná, / Guard: CF také vyžaduje [možnost/DynamicBase (použití adres náhodného generování rozložení prostoru)](dynamicbase-use-address-space-layout-randomization.md) – možnost linkeru, která je ve výchozím.

Pokud zdrojový kód je zkompilován s použitím [/Guard: CF](guard-enable-control-flow-guard.md) možnost, kompilátor analyzuje tok řízení prověřením všech nepřímé volání pro možný cíl adresy. Kompilátor vloží kód pro ověření, že je cílová adresa instrukce nepřímé volání v seznamu známých cílové adresy za běhu. Zkontrolujte operační systémy, které podporují parametr CFG zastavte program, který selže CFG runtime. To ztěžuje útočníkovi umožnit pomocí poškození dat. Chcete-li změnit cíl volání nepozorovaně spustit škodlivý kód.

Možnost/Guard: CF musí být zadána kompilátoru a linkeru, aby vytvořil povolené CFG spustitelné bitové kopie. Kód zkompilovat, ale není propojená pomocí/Guard: CF vznikly náklady kontroly za běhu, ale neumožňuje CFG ochrany. Pokud je zadána možnost/Guard: CF do `cl` příkazu kompilujete a propojujete v jednom kroku, kompilátor se předá příznak linkeru. Když **ochrany toku provádění** je nastavena v sadě Visual Studio, je možnost/Guard: CF předány kompilátoru a linkeru. Když souborů objektů nebo knihoven již byly zkompilovány samostatně, možnost musí být explicitně určena v `link` příkazu.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **Linkeru**, **příkazového řádku**.

1. V **další možnosti**, zadejte `/GUARD:CF`.

## <a name="see-also"></a>Viz také:

[/guard (povolení ochrany toku řízení)](guard-enable-control-flow-guard.md)<br/>
[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
