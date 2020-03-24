---
title: Chyba linkerů LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: 88b05512fd45adb6dc96a6c130ceccb74f3ab14e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194899"
---
# <a name="linker-tools-error-lnk1309"></a>Chyba linkerů LNK1309

> byl zjištěn modul *typ1* ; neplatné s přepínačem/CLRIMAGETYPE:*typ2*

## <a name="remarks"></a>Poznámky

Typ bitové kopie CLR byl požadován s **/CLRIMAGETYPE** , ale linker nemohl vytvořit obrázek tohoto typu, protože jeden nebo více modulů byl s tímto typem nekompatibilní.

Například se zobrazí LINKERŮ LNK1309 Pokud zadáte **/CLRIMAGETYPE: Safe** a předáte modul sestavený pomocí **/clr: Pure**.

Možnosti **/clr: Pure** a **/clr: Safe** a podpůrné knihovny jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

LINKERŮ LNK1309 se zobrazí také v případě, že se pokusíte vytvořit částečně důvěryhodnou čistě aplikaci CLR pomocí ptrustu [d]. lib. Informace o tom, jak vytvořit částečně důvěryhodnou aplikaci, naleznete v tématu [How to: Create a částečně důvěryhodné aplikace odebráním závislosti v knihovně DLL knihovny CRT](../../dotnet/create-a-partially-trusted-application.md).

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) a [/CLRIMAGETYPE (určení typu image CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).
