---
title: ATL a volné zařazování vláken
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: 94e4961c69e9441d160d72d9b72afcee3677e25f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491916"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL a volné zařazování vláken

Stránka atributů Průvodce jednoduchým objektem ATL poskytuje možnost, která umožňuje třídě agregovat volné zařazování vláken (FTM).

Průvodce generuje kód pro vytvoření instance bezplatného zařazování s vlákny v `FinalConstruct` nástroji a vydání této instance v. `FinalRelease` Makro COM_INTERFACE_ENTRY_AGGREGATE je automaticky přidáno do mapy modelu COM, aby bylo zajištěno, že `QueryInterface` žádosti pro [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) jsou zpracovávány volným zařazováním vláken.

Volné zařazování vláken umožňuje přímý přístup k rozhraním v objektu z libovolného vlákna ve stejném procesu, zrychluje volání mezi objekty Apartment. Tato možnost je určena pro třídy, které používají model dělení na vlákna.

Při použití této možnosti musí třídy převzít zodpovědnost za bezpečnost vlákna jejich dat. Kromě toho objekty, které agreguje zařazovací modul s volnými vlákny a potřebují používat ukazatele rozhraní získané z jiných objektů, musí provést další kroky, aby bylo zajištěno správné zařazování rozhraní. To obvykle zahrnuje ukládání ukazatelů rozhraní v globální tabulce rozhraní (GIT) a získání ukazatele z GITU pokaždé, když se použije. ATL poskytuje třídu [CComGITPtr](../atl/reference/ccomgitptr-class.md) , která vám může pomáhat při použití ukazatelů rozhraní uložených v Gitu.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Kdy použít globální tabulku rozhraní](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Problémy s vlákny v procesových procesech serveru](/windows/win32/com/in-process-server-threading-issues)
