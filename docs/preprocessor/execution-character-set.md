---
title: execution_character_set – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218623"
---
# <a name="execution_character_set-pragma"></a>execution_character_set – direktiva pragma

Určuje znakovou sadu spouštění použitou pro řetězcové a znakové literály. Tato direktiva není nutná pro literály označené `u8` předponou.

## <a name="syntax"></a>Syntaxe

> **#pragma execution_character_set (** "*cíl*" **)**

### <a name="parameters"></a>Parametry

*cílové*\
Určuje cílovou znakovou sadu spuštění. V současné době je jedinou podporovanou cílovou sadou spuštění znak "UTF-8".

## <a name="remarks"></a>Poznámky

Tato direktiva kompilátoru je od verze Visual Studio 2015 Update 2 zastaralá. Doporučujeme použít `/execution-charset:utf-8` Možnostikompilátoru`/utf-8` nebo spolu s použitím předponyproúzkéznakovéařetězcovéliterály,kteréobsahujírozšířenéznaky.`u8` Další informace o `u8` předponě naleznete v tématu [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md). Další informace o možnostech kompilátoru naleznete v tématu [/Execution-charset (nastavení znakové sady spuštění)](../build/reference/execution-charset-set-execution-character-set.md) a [/UTF-8. (nastavení zdrojových a spustitelných znakových sad na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

`#pragma execution_character_set("utf-8")` Direktiva instruuje kompilátor, aby ve spustitelném souboru ve vašem zdrojovém kódu zakódují zúžené a úzké řetězcové literály jako UTF-8. Toto výstupní kódování nezávisí na použitém kódování zdrojového souboru.

Ve výchozím nastavení kompilátor kóduje zúžené znaky a zúžené řetězce pomocí aktuální znakové stránky jako znaková sada spuštění. To znamená, že znaky Unicode nebo DBCS v literálu, které jsou mimo rozsah aktuální znakové stránky, jsou převedeny na výchozí nahrazující znak ve výstupu. Znaky Unicode a DBCS jsou zkráceny na jejich dolní bajt. To je téměř určitě, co byste chtěli. Můžete zadat kódování UTF-8 pro literály ve zdrojovém souboru pomocí `u8` předpony. Kompilátor předá tyto řetězce kódované v kódování UTF-8 do výstupu beze změny. Úzké znakové literály s předponou u8 se musí vejít do jednoho bajtu, nebo jsou ve výstupu zkráceny.

Ve výchozím nastavení sada Visual Studio používá aktuální znakovou stránku jako zdrojovou znakovou sadu použitou k interpretaci zdrojového kódu pro výstup. Když je soubor čten v, sada Visual Studio ho interpretuje podle aktuální znakové stránky, pokud nebyla nastavena znaková stránka souboru, nebo pokud na začátku souboru nejsou zjištěny znaky pořadí bajtů (BOM) nebo UTF-16. Vzhledem k tomu, že kódování UTF-8 nelze nastavit jako aktuální znakovou stránku, když automatické zjišťování narazí na zdrojové soubory kódované jako UTF-8 bez kusovníku, sada Visual Studio předpokládá, že jsou zakódovány pomocí aktuální znakové stránky. Znaky ve zdrojovém souboru, které jsou mimo rozsah zadané nebo automaticky rozpoznané znakové stránky, mohou způsobovat upozornění a chyby kompilátoru.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a \_ \_klíčové slovo pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/Execution-charset (nastavení znakové sady spuštění)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8 (nastavení zdrojové znakové sady a spustitelné znakové sady na UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
