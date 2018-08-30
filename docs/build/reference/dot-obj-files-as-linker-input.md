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
ms.openlocfilehash: ffbc1d7fc7f74121c37c9e80a538ec60f2265701
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219559"
---
# <a name="obj-files-as-linker-input"></a>Soubory .Obj jako vstup linkeru

Nástroj linker (odkaz. Soubor EXE) přijme soubory .obj, které jsou v Common Object File Format (COFF).

## <a name="remarks"></a>Poznámky

Společnost Microsoft poskytuje úplný popis běžný formát souborů objektu. Další informace najdete v tématu [formátu PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Podpora kódování Unicode

Od verze Visual Studio 2005, kompilátor jazyka Microsoft Visual C++ podporuje znaky znakové sady Unicode v identifikátorech definované ISO/IEC C a C++ standardy. Předchozí verze kompilátoru podporovány v identifikátorech pouze znaky ASCII. Pro podporu kódování Unicode v názvy funkcí, tříd a statické, kompilátoru a propojovacího programu je používat kódování Unicode UTF-8 symbolů COFF v souborech .obj. Kódování UTF-8 je upwardly kompatibilní s kódováním ASCII, které se používají v předchozích verzích sady Visual Studio.

Další informace o kompilátoru a linkeru, naleznete v tématu [Podpora kódování Unicode v kompilátoru a Linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Další informace o standardu Unicode, najdete v článku [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organizace.

## <a name="see-also"></a>Viz také:

[Vstupní soubory LINK](../../build/reference/link-input-files.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
[Podpora pro Unicode](../../text/support-for-unicode.md)  
[Podpora kódování Unicode v kompilátoru a linkeru](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Unicode standard](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formátu PE](/windows/desktop/Debug/pe-format)  
