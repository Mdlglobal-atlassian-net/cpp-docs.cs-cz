---
title: Agregace a makra factory tříd
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: 33f33043d1a2c824ada26399365541796178d21d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319340"
---
# <a name="aggregation-and-class-factory-macros"></a>Agregace a makra factory tříd

Tato makra poskytují způsoby řízení agregace a deklarování třídy továrny.

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|Deklaruje, že objekt lze agregovat (výchozí).|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|Deklaruje factory třídy [ccomclassfactory](../../atl/reference/ccomclassfactory-class.md), atl výchozí třídy factory.|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|Deklaruje objekt factory třídy jako factory třídy.|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako factory třídy.|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako factory třídy.|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako factory třídy.|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|Deklaruje virtuální `GetControllingUnknown` funkci.|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|Deklaruje, že objekt nelze agregovat.|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|Deklaruje, že váš objekt musí být agregovány.|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|Zkontroluje hodnotu vnější neznámý a deklaruje objekt agregatable nebo není agregatable, podle potřeby.|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|Chrání vnější objekt před odstraněním během konstrukce vnitřního objektu.|
|[DECLARE_VIEW_STATUS](#declare_view_status)|Určuje příznaky VIEWSTATUS do kontejneru.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="declare_aggregatable"></a><a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE

Určuje, že objekt lze agregovat.

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy, kterou definujete jako agregovatelnou.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje toto makro k určení výchozího modelu agregace. Chcete-li toto výchozí nastavení přepsat, zadejte v definici třídy [DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable) nebo [DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable) makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_classfactory"></a><a name="declare_classfactory"></a>DECLARE_CLASSFACTORY

Deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako factory třídy.

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) používá toto makro k deklarování výchozí třídy pro váš objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

## <a name="ccomclassfactory-class"></a><a name="ccomclassfactory_class"></a>Třída CComClassFactory

Tato třída implementuje rozhraní [IClassFactory.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Poznámky

`CComClassFactory`implementuje rozhraní [IClassFactory,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) které obsahuje metody pro vytvoření objektu určitého identifikátoru CLSID, stejně jako uzamčení factory třídy v paměti, aby bylo možné rychleji vytvářet nové objekty. `IClassFactory`musí být implementována pro každou třídu, kterou zaregistrujete v systémovém registru a ke které přiřadíte CLSID.

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [makro DECLARE_CLASSFACTORY](#declare_classfactory) `CComClassFactory` , který deklaruje jako výchozí třídy factory. Chcete-li toto výchozí nastavení přepsat, zadejte jedno z makra DECLARE_CLASSFACTORY*XXX* v definici třídy. Například [makro DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex) používá zadanou třídu pro třídu factory:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

Výše uvedená definice `CMyClassFactory` třídy určuje, že bude použit jako objekt u výchozí třídy factory. `CMyClassFactory`musí odvodit a `CComClassFactory` přepsat `CreateInstance`.

Atl poskytuje tři další makra, která deklarují třídy:

- [DECLARE_CLASSFACTORY2](#declare_classfactory2) Používá [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), který řídí vytváření prostřednictvím licence.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) Používá [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), který vytváří objekty ve více bytech.

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) Používá [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), který vytvoří jeden [cComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) objekt.

## <a name="declare_classfactory_ex"></a><a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX

Deklaruje, že je továrna třídy. `cf`

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
[v] Název třídy, která implementuje objekt factory třídy.

### <a name="remarks"></a>Poznámky

Parametr *cf* musí být odvozen z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a přepsat metodu. `CreateInstance`

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_CLASSFACTORY](#declare_classfactory) makro, `CComClassFactory` které určuje jako výchozí třídy factory. Zahrnutím DECLARE_CLASSFACTORY_EX makra do definice třídy objektu však toto výchozí nastavení přepíšete.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

## <a name="declare_classfactory2"></a><a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2

Deklaruje [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) jako factory třídy.

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>Parametry

*Lic*<br/>
[v] Třída, která `VerifyLicenseKey`implementuje , `GetLicenseKey`a `IsLicenseValid`.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [makro DECLARE_CLASSFACTORY,](#declare_classfactory) které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Zahrnutím DECLARE_CLASSFACTORY2 makra do definice třídy objektu však toto výchozí nastavení přepíšete.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

## <a name="ccomclassfactory2-class"></a><a name="ccomclassfactory2_class"></a>Třída CComClassFactory2

Tato třída implementuje rozhraní [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>Parametry

*Licence*<br/>
Třída, která implementuje následující statické funkce:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>Poznámky

`CComClassFactory2`implementuje rozhraní [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) které je rozšířením [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`řídí vytváření objektů prostřednictvím licence. Továrna třídy spuštěná na licencovaném počítači může poskytnout licenční klíč za běhu. Tento licenční klíč umožňuje aplikaci vytvářet instance objektů, pokud neexistuje úplná licence počítače.

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory)maker , který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Chcete-li použít `CComClassFactory2`, zadejte [DECLARE_CLASSFACTORY2](#declare_classfactory2) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`, musí parametr `CComClassFactory2`šablony do aplikace `VerifyLicenseKey` `GetLicenseKey`implementovat `IsLicenseValid`statické funkce , a . Následuje příklad jednoduché třídy licencí:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2`pochází z `CComClassFactory2Base` obou a *licence*. `CComClassFactory2Base`, podle pořadí, `IClassFactory2` pochází z a **CComObjectRootEx\< CComGlobalsThreadModel >**.

## <a name="declare_classfactory_auto_thread"></a><a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD

Deklaruje [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako factory třídy.

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [makro DECLARE_CLASSFACTORY,](#declare_classfactory) které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Zahrnutím DECLARE_CLASSFACTORY_AUTO_THREAD makra do definice třídy objektu však toto výchozí nastavení přepíšete.

Při vytváření objektů ve více bytech (na serveru mimo proc) přidejte DECLARE_CLASSFACTORY_AUTO_THREAD do třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="ccomclassfactoryautothread-class"></a><a name="ccomclassfactoryautothread_class"></a>Třída CComClassFactoryAutoThread

Tato třída implementuje rozhraní [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) a umožňuje objekty, které mají být vytvořeny ve více bytech.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>Poznámky

`CComClassFactoryAutoThread`je podobný [CComClassFactory](../../atl/reference/ccomclassfactory-class.md), ale umožňuje objekty, které mají být vytvořeny ve více bytech. Chcete-li využít této podpory, odvodit modul EXE z [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [DECLARE_CLASSFACTORY](#declare_classfactory)maker , který deklaruje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Chcete-li použít `CComClassFactoryAutoThread`, zadejte [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

## <a name="declare_classfactory_singleton"></a><a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON

Deklaruje [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md) jako factory třídy.

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>Parametry

*Obj*<br/>
[v] Název objektu třídy.

### <a name="remarks"></a>Poznámky

[CComCoClass](../../atl/reference/ccomcoclass-class.md) obsahuje [makro DECLARE_CLASSFACTORY,](#declare_classfactory) které určuje [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) jako výchozí třídy factory. Zahrnutím DECLARE_CLASSFACTORY_SINGLETON makra do definice třídy objektu však toto výchozí nastavení přepíšete.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="ccomclassfactorysingleton-class"></a><a name="ccomclassfactorysingleton_class"></a>Třída CComClassFactorySingleton

Tato třída je odvozena od [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída.

`CComClassFactorySingleton`pochází z [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) a používá [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) k vytvoření jednoho objektu. Každé volání `CreateInstance` metody jednoduše dotazuje tento objekt na ukazatel rozhraní.

### <a name="remarks"></a>Poznámky

Objekty ATL obvykle získávají třídu odvozením z [CComCoClass](../../atl/reference/ccomcoclass-class.md). Tato třída zahrnuje [makro DECLARE_CLASSFACTORY](#declare_classfactory) `CComClassFactory` , který deklaruje jako výchozí třídy factory. Chcete-li použít `CComClassFactorySingleton`, zadejte [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton) makro v definici třídy objektu. Příklad:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

## <a name="declare_get_controlling_unknown"></a><a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN

Deklaruje `GetControllingUnknown`virtuální funkci .

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>Poznámky

Toto makro přidejte do objektu, pokud `GetControllingUnknown` se zobrazí chybová `CComAggregateCreator`zpráva kompilátoru, která není definována (například v ).

## <a name="declare_not_aggregatable"></a><a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE

Určuje, že objekt nelze agregovat.

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název objektu třídy, který definujete jako neagregatable.

### <a name="remarks"></a>Poznámky

DECLARE_NOT_AGGREGATABLE `CreateInstance` způsobí, že vrátí chybu (CLASS_E_NOAGGREGATION), pokud je proveden pokus o agregaci na objekt.

Ve výchozím nastavení [ccomcoclass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makro, které určuje, že objekt lze agregovat. Chcete-li toto výchozí chování přepsat, zahrňte DECLARE_NOT_AGGREGATABLE do definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

## <a name="declare_only_aggregatable"></a><a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE

Určuje, že objekt musí být agregován.

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název objektu třídy, který definujete jako pouze agregovatelný.

### <a name="remarks"></a>Poznámky

DECLARE_ONLY_AGGREGATABLE způsobí chybu (E_FAIL), pokud je `CoCreate` proveden pokus o objekt jako neagregovaný objekt.

Ve výchozím nastavení [ccomcoclass](../../atl/reference/ccomcoclass-class.md) obsahuje [DECLARE_AGGREGATABLE](#declare_aggregatable) makro, které určuje, že objekt lze agregovat. Chcete-li toto výchozí chování přepsat, zahrňte DECLARE_ONLY_AGGREGATABLE do definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

## <a name="declare_poly_aggregatable"></a><a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE

Určuje, že instance ** \< CComPolyObject** *x* **>** je vytvořena při vytvoření objektu.

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název objektu třídy, který definujete jako agregovatelný nebo není agregovatelný.

### <a name="remarks"></a>Poznámky

Během vytváření je zkontrolována hodnota vnějšího neznámého. Pokud je NULL, `IUnknown` je implementována pro neagregovaný objekt. Pokud vnější neznámý není `IUnknown` NULL, je implementována pro agregovaný objekt.

Výhodou použití DECLARE_POLY_AGGREGATABLE je, že `CComAggObject` se `CComObject` vyhnete tomu, abyste měli oba a v modulu pro zpracování agregovaných a neagregovaných případů. Jeden `CComPolyObject` objekt zpracovává oba případy. To znamená, že ve vašem modulu existuje pouze jedna kopie vtable a jedna kopie funkcí. Pokud je vaše vtable je velký, to může podstatně snížit velikost modulu. Pokud je však vaše vtable malá, může použití `CComPolyObject` způsobit o něco větší velikost modulu, protože není `CComAggObject` optimalizována pro agregovaný nebo neagregovaný objekt, jako jsou a . `CComObject`

Pokud použijete Průvodce řízením knihovny ATL k vytvoření úplného ovládacího prvku, bude makro DECLARE_POLY_AGGREGATABLE automaticky deklarováno v objektu.

## <a name="declare_protect_final_construct"></a><a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT

Chrání objekt před odstraněním, pokud (během [FinalConstruct)](ccomobjectrootex-class.md#finalconstruct)vnitřní agregovaný objekt zvětší počet odkazů pak sníží počet na 0.

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

## <a name="declare_view_status"></a><a name="declare_view_status"></a>DECLARE_VIEW_STATUS

Umístěte toto makro do třídy řízení activex atl a určete příznaky VIEWSTATUS do kontejneru.

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>Parametry

*statusFlags*<br/>
[v] ViewSTATUS příznaky. Seznam příznaků naleznete v tématu [VIEWSTATUS.](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
