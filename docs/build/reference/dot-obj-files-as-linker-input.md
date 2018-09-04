---
title: . Soubory obj jako vstup Linkeru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd1fbd635b1d3d3a5f9963edaa9f22e22472dad1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691748"
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj linker (odkaz. Soubor EXE) přijme soubory .obj, které jsou v Common Object File Format (COFF).

## <a name="remarks"></a>Poznámky

Společnost Microsoft poskytuje úplný popis běžný formát souborů objektu. Další informace najdete v tématu [formátu PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Podpora kódování Unicode

Od verze Visual Studio 2005, kompilátor jazyka Microsoft Visual C++ podporuje znaky znakové sady Unicode v identifikátorech definované ISO/IEC C a C++ standardy. Předchozí verze kompilátoru podporovány v identifikátorech pouze znaky ASCII. Pro podporu kódování Unicode v názvy funkcí, tříd a statické, kompilátoru a propojovacího programu je používat kódování Unicode UTF-8 symbolů COFF v souborech .obj. Kódování UTF-8 je upwardly kompatibilní s kódováním ASCII, které se používají v předchozích verzích sady Visual Studio.

Další informace o kompilátoru a linkeru, naleznete v tématu [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode, najdete v článku [Unicode](http://www.unicode.org/) organizace.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](../../build/reference/link-input-files.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
[Podpora pro Unicode](../../text/support-for-unicode.md)  
[Podpora kódování Unicode v kompilátoru a linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode standard](http://www.unicode.org/)  
[Formátu PE](/windows/desktop/Debug/pe-format)  
