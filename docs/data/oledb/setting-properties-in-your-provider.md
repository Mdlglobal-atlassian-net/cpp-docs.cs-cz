---
title: Nastavení vlastností ve zprostředkovateli
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 905a9bb32544dbd7453d46362e100047516d22a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209570"
---
# <a name="setting-properties-in-your-provider"></a>Nastavení vlastností ve zprostředkovateli

Vyhledejte skupinu vlastností a ID vlastnosti požadované vlastnosti. Další informace najdete v tématu [OLE DB vlastnosti](/previous-versions/windows/desktop/ms722734(v=vs.85)) v **referenci programátora OLE DB**.

V kódu poskytovatele generovaném průvodcem vyhledejte mapu vlastností odpovídající skupině vlastností. Název skupiny vlastností obvykle odpovídá názvu objektu. Vlastnosti příkazu a sady řádků lze nalézt v příkazu nebo sadě řádků; zdroj dat a inicializační vlastnosti lze nalézt v objektu zdroje dat.

V mapě vlastností přidejte [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) makro. PROPERTY_INFO_ENTRY_EX používá čtyři parametry:

- ID vlastnosti odpovídající vaší vlastnosti. Odebere prvních sedm znaků ("DBPROP_") od začátku názvu vlastnosti. Například pokud chcete přidat `DBPROP_MAXROWS`, předejte `MAXROWS` jako první prvek. Pokud se jedná o vlastní vlastnost, předejte úplný název GUID (například `DBMYPROP_MYPROPERTY`).

- Typ variant vlastnosti (v [OLE DB vlastnosti](/previous-versions/windows/desktop/ms722734(v=vs.85)) v **odkazu programátora OLE DB**). Zadejte typ VT_ (například VT_BOOL nebo VT_I2) odpovídající datovému typu.

- Příznaky k označení, zda je vlastnost čitelná a zapisovatelné a skupina, do které patří. Například následující kód indikuje vlastnost pro čtení/zápis patřící do skupiny sady řádků:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Základní hodnota vlastnosti To může být například `VARIANT_FALSE` pro logický typ nebo nula pro typ integer, například. Vlastnost má tuto hodnotu, pokud se nezmění.

    > [!NOTE]
    > Některé vlastnosti jsou připojené nebo zřetězené na jiné vlastnosti, jako jsou například záložky nebo aktualizace. Když příjemce nastaví jednu vlastnost na hodnotu true, může být nastavena i jiná vlastnost. Šablony poskytovatele OLE DB tuto podporu podporují prostřednictvím metody [CUtlProps::-PropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md).

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Vlastnosti ignorované poskytovateli OLE DB Microsoftu

Poskytovatelé Microsoft OLE DB ignorují následující vlastnosti OLE DB:

- `DBPROP_MAXROWS` funguje pouze pro poskytovatele jen pro čtení (to znamená, kde `DBPROP_IRowsetChange` a `DBPROP_IRowsetUpdate` jsou **nepravdivé**); v opačném případě tato vlastnost není podporována.

- `DBPROP_MAXPENDINGROWS` se ignoruje. Zprostředkovatel určuje vlastní limit.

- `DBPROP_MAXOPENROWS` se ignoruje. Zprostředkovatel určuje vlastní limit.

- `DBPROP_CANHOLDROWS` se ignoruje. Zprostředkovatel určuje vlastní limit.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
