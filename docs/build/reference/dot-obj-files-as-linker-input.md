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
ms.openlocfilehash: 3e02ccc09ae8c9c2f3df88bc1767ff0188baa1f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492942"
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj Linker (odkaz. EXE) přijímá soubory. obj, které jsou ve formátu COFF (Common Object File Format).

## <a name="remarks"></a>Poznámky

Microsoft poskytuje úplný popis formátu Common Object File. Další informace najdete v tématu [Formát PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Podpora kódování Unicode

Počínaje sadou Visual Studio 2005 kompilátor Microsoft MSVC podporuje znaky Unicode v identifikátorech definovaných normami ISO/IEC C a C++ . Předchozí verze kompilátoru podporovaly v identifikátorech pouze znaky ASCII. Pro podporu kódování Unicode v názvech funkcí, tříd a statických verzí kompilátor a Linker používá kódování Unicode UTF-8 pro symboly COFF v souborech. obj. Kódování UTF-8 je v souladu s kódováním ASCII používaným v dřívějších verzích sady Visual Studio.

Další informace o kompilátoru a linkeru naleznete v tématu [Podpora kódování Unicode v kompilátoru a linkeru](unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode najdete v tématu organizace [Unicode](https://www.unicode.org/) .

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](link-input-files.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[Podpora pro Unicode](../../text/support-for-unicode.md)<br/>
[Podpora kódování Unicode v kompilátoru a linkeru](unicode-support-in-the-compiler-and-linker.md)<br/>
[Standard Unicode](https://www.unicode.org/)<br/>
[Formát PE](/windows/win32/Debug/pe-format)
