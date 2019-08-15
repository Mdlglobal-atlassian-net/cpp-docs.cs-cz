---
title: CMutex – třída
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 65f7f4db9489de1c9a380d760ed5cab41bfdc2ec
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504523"
---
# <a name="cmutex-class"></a>CMutex – třída

Představuje "mutex" – synchronizační objekt, který umožňuje jednomu vláknu vzájemně exkluzivní přístup k prostředku.

## <a name="syntax"></a>Syntaxe

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|`CMutex` Vytvoří objekt.|

## <a name="remarks"></a>Poznámky

Mutexy jsou užitečné v případě, že může být povoleno pouze jedno vlákno v jednom okamžiku upravovat data nebo jiný kontrolovaný prostředek. Například přidání uzlů do propojeného seznamu je proces, který by měl být povolen pouze v jednom vlákně. Při použití `CMutex` objektu k řízení propojeného seznamu může přístup k tomuto seznamu získat pouze jedno vlákno v jednom okamžiku.

Chcete-li `CMutex` použít objekt, `CMutex` Sestavte objekt, když je potřeba. Zadejte název mutexu, na kterém chcete čekat, a aplikaci, kterou by měla aplikace zpočátku vlastnit. Po návratu konstruktoru můžete přístup k objektu mutex získat. Zavolejte [CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) , když jste dokončili přístup k řízenému prostředku.

Alternativním způsobem použití `CMutex` objektů je přidat proměnnou typu `CMutex` jako datový člen do třídy, kterou chcete ovládat. Během konstrukce kontrolovaného objektu zavolejte konstruktor `CMutex` datového členu, který určuje, zda je mutex původně vlastněn, název mutex (Pokud bude použit napříč hranicemi procesu) a požadované atributy zabezpečení.

Chcete-li získat přístup `CMutex` k prostředkům řízenými objekty tímto způsobem, nejprve vytvořte proměnnou typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo do funkce člena přístupu prostředku zadejte [CMultiLock](../../mfc/reference/cmultilock-class.md) . Pak zavolejte `Lock` členskou funkci objektu zámku (například [CSingleLock:: Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vaše vlákno získá přístup k prostředku, počká na uvolnění prostředku a získá přístup, nebo počkejte na uvolnění prostředku a vypršení časového limitu, čímž se nepodaří získat přístup k prostředku. V každém případě byl k vašemu prostředku přístup bezpečným způsobem. Chcete-li uvolnit prostředek, použijte `Unlock` členskou funkci objektu zámku (například [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo umožněte objektu zámku, aby se z oboru nevrátil.

Další informace o použití `CMutex` objektů naleznete v článku [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt. h

##  <a name="cmutex"></a>CMutex::CMutex

Vytvoří pojmenovaný nebo nepojmenovaný `CMutex` objekt.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Určuje, zda vlákno vytvářející `CMutex` objekt zpočátku má přístup k prostředku kontrolovanému mutex.

*lpszName*<br/>
`CMutex` Název objektu. Pokud je k dispozici jiný mutex se stejným názvem, je nutné zadat *lpszName* , pokud se objekt bude používat napříč hranicemi procesu. Pokud **má hodnotu null**, mutex nebude pojmenovaný. Pokud se název shoduje s existujícím mutex, konstruktor vytvoří nový `CMutex` objekt, který odkazuje na mutex daného názvu. Pokud se název shoduje se stávajícím synchronizačním objektem, který není mutex, konstrukce se nezdaří.

*lpsaAttribute*<br/>
Atributy zabezpečení pro objekt mutex Úplný popis této struktury naleznete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat přístup `CMutex` k objektu nebo ho uvolnit, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho funkci [Lock](../../mfc/reference/csinglelock-class.md#lock) a [Odemkněte](../../mfc/reference/csinglelock-class.md#unlock) členské funkce. Pokud se `Unlock` objekt používá samostatně, zavolejte jeho členskou funkci a uvolněte ji. `CMutex`

> [!IMPORTANT]
>  Po vytvoření `CMutex` objektu použijte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby se zajistilo, že mutex ještě neexistuje. Pokud Mutex neočekávaně existoval, může to znamenat, že neoprávněný proces je squatting a může vycházet z škodlivého použití mutexu. V tomto případě je doporučený postup pro zaznamenání zabezpečení zavřít a pokračovat, jako kdyby došlo k chybě při vytváření objektu.

## <a name="see-also"></a>Viz také:

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
