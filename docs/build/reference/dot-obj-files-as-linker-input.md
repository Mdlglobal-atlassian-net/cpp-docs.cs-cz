---
title: Soubory .Obj jako vstup linkeru
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 17a8ea51c41fb2c17d8feb223253cf9eed722675
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616148"
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj linker (odkaz. Soubor EXE) přijme soubory .obj, které jsou v Common Object File Format (COFF).

## <a name="remarks"></a>Poznámky

Společnost Microsoft poskytuje úplný popis běžný formát souborů objektu. Další informace najdete v tématu [formátu PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Podpora kódování Unicode

Od verze Visual Studio 2005, kompilátor jazyka Microsoft Visual C++ podporuje znaky znakové sady Unicode v identifikátorech definované ISO/IEC C a C++ standardy. Předchozí verze kompilátoru podporovány v identifikátorech pouze znaky ASCII. Pro podporu kódování Unicode v názvy funkcí, tříd a statické, kompilátoru a propojovacího programu je používat kódování Unicode UTF-8 symbolů COFF v souborech .obj. Kódování UTF-8 je upwardly kompatibilní s kódováním ASCII, které se používají v předchozích verzích sady Visual Studio.

Další informace o kompilátoru a linkeru, naleznete v tématu [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode, najdete v článku [Unicode](http://www.unicode.org/) organizace.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](../../build/reference/link-input-files.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[Podpora pro Unicode](../../text/support-for-unicode.md)<br/>
[Podpora kódování Unicode v kompilátoru a linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md)<br/>
[Unicode standard](http://www.unicode.org/)<br/>
[Formátu PE](/windows/desktop/Debug/pe-format)
