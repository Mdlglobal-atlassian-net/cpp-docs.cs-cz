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
ms.openlocfilehash: 304c9861b85be1925e48d47c6006fcbcdd41dc22
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791594"
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj Linker (odkaz. EXE) přijímá soubory. obj, které jsou ve formátu COFF (Common Object File Format).

## <a name="remarks"></a>Poznámky

Microsoft poskytuje úplný popis formátu Common Object File. Další informace najdete v tématu [Formát PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Podpora kódování Unicode

Počínaje sadou Visual Studio 2005 kompilátor Microsoft MSVC podporuje znaky Unicode v identifikátorech definovaných normami ISO/IEC C a C++ . Předchozí verze kompilátoru podporovaly v identifikátorech pouze znaky ASCII. Pro podporu kódování Unicode v názvech funkcí, tříd a statických verzí kompilátor a Linker používá kódování Unicode UTF-8 pro symboly COFF v souborech. obj. Kódování UTF-8 je v souladu s kódováním ASCII používaným v dřívějších verzích sady Visual Studio.

Další informace o kompilátoru a linkeru naleznete v tématu [Podpora kódování Unicode v kompilátoru a linkeru](unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode najdete v tématu organizace [Unicode](https://home.unicode.org/) .

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](link-input-files.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[Podpora pro Unicode](../../text/support-for-unicode.md)<br/>
[Podpora kódování Unicode v kompilátoru a linkeru](unicode-support-in-the-compiler-and-linker.md)<br/>
[Standard Unicode](https://home.unicode.org/)<br/>
[Formát PE](/windows/win32/Debug/pe-format)
