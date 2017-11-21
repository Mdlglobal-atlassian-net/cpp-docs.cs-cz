---
title: "Předávání testů shodnosti technologie OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8ef7e32f56fdff81c7a66a1dfcc6c613201e2f49
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="passing-ole-db-conformance-tests"></a>Předávání testů shodnosti technologie OLE DB
Chcete-li více konzistentní zprostředkovatelé, Data Access SDK poskytuje sadu testů shodnosti technologie OLE DB. Testy zkontrolujte všechny aspekty svého poskytovatele a získáte přiměřenou jistotu, že váš zprostředkovatel funguje podle očekávání. Můžete najít testů shodnosti technologie OLE DB na Microsoft Data Access SDK. Tato část se zaměřuje na věcí, které byste měli udělat předávání testů shodnosti. Informace o spuštění testů shodnosti technologie OLE DB naleznete v sadě SDK.  
  
## <a name="running-the-conformance-tests"></a>Spuštění testů shodnosti  
 Ve Visual C++ 6.0 přidali šablony zprostředkovatele technologie OLE DB počet zapojených funkcí, které vám umožní zkontrolujte hodnoty a vlastnosti. Většina těchto funkcí byly přidány v reakci na testů shodnosti.  
  
> [!NOTE]
>  Je nutné přidat několik ověřovacích funkcí pro váš poskytovatel předávání testů shodnosti technologie OLE DB.  
  
 Tento zprostředkovatel vyžaduje dvě rutiny ověřování. První rutina `CRowsetImpl::ValidateCommandID`, je součástí vaší třídy sady řádků. Při vytváření sady řádků je volána metodou šablony zprostředkovatele. Ukázka používá tuto rutinu příjemci říct, že nepodporuje indexy. První volání je `CRowsetImpl::ValidateCommandID` (Všimněte si, že používá zprostředkovatel **_RowsetBaseClass** typedef přidat v mapě rozhraní pro `CMyProviderRowset` v [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md), takže není nutné Zadejte tyto dlouhé řádky argumenty šablony). Pak se vraťte **DB_E_NOINDEX** Pokud není parametr indexu **NULL** (to znamená, chce příjemce na nás použít index). Další informace o ID příkazů najdete v OLE DB specifikaci a vyhledejte **IOpenRowset::OpenRowset**.  
  
 Následující kód je **ValidateCommandID –** ověření rutiny:  
  
```  
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
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
  
 Šablony zprostředkovatele volají `OnPropertyChanged` metoda vždy, když někdo změní vlastnost na **DBPROPSET_ROWSET** skupiny. Pokud chcete zpracovat vlastnosti pro další skupiny, je přidáte do příslušného objektu (to znamená, **DBPROPSET_SESSION** kontroly přejděte `CMyProviderSession` třídy).  
  
 Kód nejdřív zkontroluje, zda je vlastnost propojena do jiného. Pokud je vlastnost zřetězená, nastaví **DBPROP_BOOKMARKS** vlastnost na hodnotu True. Příloha C specifikace OLE DB obsahuje informace o vlastnostech. Tyto informace taky poznáte, jestli je vlastnost zřetězená do jiné.  
  
 Můžete také přidat `IsValidValue` rutiny do vašeho kódu. Volání šablony `IsValidValue` při pokusu o nastavení vlastnosti. Tato metoda by se mělo přepsat, pokud požadujete další zpracování při nastavení hodnoty vlastnosti. Může mít jednu z těchto metod pro každou sadu vlastností.  
  
## <a name="threading-issues"></a>Problémy dělení na vlákna  
 Ve výchozím nastavení Průvodce zprostředkovatele OLE DB v průvodci zprostředkovatele OLE DB ATL generuje kód pro zprostředkovatele pro spuštění v modelu typu apartment. Pokud se uživatel pokusí spustit tento kód s testů shodnosti, obdržíte nejprve selhání. To je vzhledem k tomu, že Ltm.exe, nástroj, který slouží ke spuštění testů shodnosti technologie OLE DB, použije se výchozí hodnota volného vláken. Kód Průvodce zprostředkovatele technologie OLE DB výchozí modelu objektu apartment výkonu a snadného použití.  
  
 Chcete-li tento problém, můžete buď změnit LTM nebo změnit zprostředkovatele.  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>Chcete-li změnit LTM pro spuštění v objektu apartment režimu vláken  
  
1.  V hlavní nabídce LTM klikněte na tlačítko **nástroje**a potom klikněte na **možnosti**.  
  
2.  Na **Obecné** změňte model vláken z **volné zařazování** k **Apartment Threaded**.  
  
 Chcete-li změnit zprostředkovatele pro spuštění v režimu Volné zařazování:  
  
-   V projektu poskytovatele vyhledávání pro všechny instance `CComSingleThreadModel` a nahraďte ho `CComMultiThreadModel`, což by mělo být v záhlaví svých datového zdroje, relace a sady řádků.  
  
-   Ve vašem souboru .rgs změňte model vláken z **Apartment** k **i**.  
  
-   Postupujte podle správných pravidel programování pro programování volného zřetězení (tedy uzamknout zápisy).  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)