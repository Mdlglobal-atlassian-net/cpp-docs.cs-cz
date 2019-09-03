---
title: '#undef – direktiva (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: 1a69bc568579e7da7c7e3816cb67c8153b8f1a27
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220215"
---
# <a name="undef-directive-cc"></a>#undef direktiva (CC++/)

Odebere (zruší definici) název dříve vytvořený pomocí direktivy `#define`.

## <a name="syntax"></a>Syntaxe

> **#undef** *identifikátor*

## <a name="remarks"></a>Poznámky

Direktiva **#undef** odstraní aktuální definici identifikátoru. V důsledku toho jsou další výskyty *identifikátoru* ignorovány preprocesorem. Chcete-li odebrat definici makra pomocí **#undef**, zadejte pouze *identifikátor*makra, nikoli seznam parametrů.

Direktivu **#undef** můžete použít také pro identifikátor, který nemá žádnou předchozí definici. Tím je zajištěno, že tento identifikátor není definován. Nahrazení makra není provedeno v rámci příkazů **#undef** .

Direktiva **#undef** je obvykle spárována s `#define` direktivou pro vytvoření oblasti ve zdrojovém programu, ve které má identifikátor zvláštní význam. Určitá funkce zdrojového programu například může použít konstanty manifestu pro definování hodnot specifických pro prostředí, které nemají vliv na zbytek programu. Direktiva **#undef** také pracuje s `#if` direktivou pro řízení podmíněné kompilace zdrojového programu. Další informace najdete v tématu [direktivy #if, #elif, #else a #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

V následujícím příkladu direktiva **#undef** odebere definice symbolické konstanty a makra. Je uveden pouze identifikátor makra.

```C
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Specifické pro společnost Microsoft**

Makra lze z příkazového řádku nedefinovat pomocí `/U` možnosti, následovaná názvy maker, které mají být nedefinovány. Účinek vystavení tohoto příkazu je ekvivalentem posloupnosti `#undef` příkazů *názvu makra* na začátku souboru.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
