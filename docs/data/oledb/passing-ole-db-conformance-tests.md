---
title: Předávání testů shodnosti technologie OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: f7c5435003866e2c3490bd07e28ec10eca0ec0cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491712"
---
# <a name="passing-ole-db-conformance-tests"></a>Předávání testů shodnosti technologie OLE DB

Chcete-li poskytovatele konzistentnější, Data Access SDK poskytuje sadu testů shodnosti technologie OLE DB. Testy zkontrolujte všechny aspekty vašeho poskytovatele a poskytují rozumné záruku, že vaše zprostředkovatel funguje podle očekávání. Testů shodnosti technologie OLE DB můžete najít v sadě Microsoft Data Access SDK. Tato část se zaměřuje na věci, které byste měli udělat pro předávání testů shodnosti. Informace o spuštění testů shodnosti technologie OLE DB najdete v sadě SDK.

## <a name="running-the-conformance-tests"></a>Spuštění testů shodnosti

Ve Visual C++ 6.0 přidali šablony zprostředkovatele OLE DB počet zapojených funkcí, které umožňují zkontrolovat hodnoty a vlastnosti. Většina těchto funkcí byly přidány v reakci na testů shodnosti.

> [!NOTE]
> Budete muset přidat několik ověřovací funkce pro předávání testů shodnosti technologie OLE DB poskytovatele.

Tento poskytovatel vyžaduje dvě rutiny ověřování. První rutina `CRowsetImpl::ValidateCommandID`, je součástí vaší třídy sady řádků. Je volána při vytváření sady řádků šablony zprostředkovatele. Ukázka používá tato rutina příjemci říct, že nepodporuje indexy. První volání `CRowsetImpl::ValidateCommandID` (Všimněte si, že poskytovatel použije `_RowsetBaseClass` typedef přidán v mapě rozhraní pro `CCustomRowset` v [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md), takže není potřeba psát tyto dlouhé řádky šablony argumenty). Pokud parametr indexu není NULL, pak se vraťte DB_E_NOINDEX (označuje, že uživatel chce používat indexu v USA). Další informace o ID příkazů najdete v příslušné specifikaci OLE DB a hledejte `IOpenRowset::OpenRowset`.

Následující kód je `ValidateCommandID` ověření rutinu:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Šablony zprostředkovatele volají `OnPropertyChanged` metoda pokaždé, když někdo změní vlastnost na `DBPROPSET_ROWSET` skupiny. Pokud chcete zpracovávat vlastnosti pro jiné skupiny, je přidáte do příslušného objektu (to znamená, `DBPROPSET_SESSION` kontroly přejdou do `CCustomSession` třídy).

Kód nejprve zkontroluje, zda je vlastnost propojený na jiný. Když se tato vlastnost je zřetězená, nastaví `DBPROP_BOOKMARKS` vlastnost `True`. Příloha C specifikaci OLE DB obsahuje informace o vlastnostech. Tyto informace také zjistíte, zda je vlastnost zřetězené do jiného.

Můžete také přidat `IsValidValue` rutiny do vašeho kódu. Volání šablony `IsValidValue` při pokusu o nastavení vlastnosti. Tato metoda by se mělo přepsat, pokud vyžadují další zpracování při nastavení hodnoty vlastnosti. Můžete mít jednu z těchto metod pro každou sadu vlastností.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)