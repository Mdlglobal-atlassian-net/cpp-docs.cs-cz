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
ms.openlocfilehash: ddea5a74dbd40d097398d04c0b2bc274df5ec972
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299995"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL a volné zařazování vláken

Stránka ATL Průvodce jednoduchým objektem na atributy poskytuje možnost, která umožňuje vaší třídy k agregaci volné zařazování vláken (FTM).

Průvodce vygeneruje kód, který vytvoří instanci volné zařazování vláken v `FinalConstruct` a vydání této instance v `FinalRelease`. Makro COM_INTERFACE_ENTRY_AGGREGATE se automaticky přidá do mapy modelu COM a zkontrolujte, že `QueryInterface` žádosti o [rozhraní IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal) jsou zpracovávány volné zařazování vláken.

Volné zařazování vláken, umožňuje přímý přístup k rozhraní na objekt z libovolného vlákna ve stejném procesu, urychluje volání mezi objektu apartment. Tato možnost je určená pro třídy, které používají obě modelu vláken.

Při použití této možnosti třídy musí nést odpovědnost za zabezpečení vlákna svá data. Kromě toho objekty, které potřebují použít ukazatele rozhraní získané od jiných objektů a agregovat volné zařazování vláken musejí udělat dodatečné kroky k zajištění, že jsou správně zařadit rozhraní. Obvykle to zahrnuje ukládání ukazatele rozhraní do tabulky globálního rozhraní (GIT) a získávání ukazatele z GITU pokaždé, když se používá. Knihovna ATL poskytuje třídu [ccomgitptr –](../atl/reference/ccomgitptr-class.md) můžete použít ukazatele rozhraní, které jsou uložené v GITU.

## <a name="see-also"></a>Viz také:

[Koncepty](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/desktop/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/desktop/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Kdy použít tabulky globálního rozhraní](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Proces serveru potíže s vlákny](/windows/desktop/com/in-process-server-threading-issues)
