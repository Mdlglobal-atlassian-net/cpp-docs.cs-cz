---
title: 'Postupy: definování a instalace globální obslužné rutiny výjimek | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ff91a742b1a6641fbc689968587f0472c333e16a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423354"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Postupy: Definování a instalace globální obslužné rutiny výjimek

Následující příklad kódu ukazuje, jak neošetřené výjimky mohou být zachyceny. Ukázkový formulář obsahuje tlačítka, který při stisknutí, provádí odkaz s hodnotou null, což způsobí vyvolání výjimky. Tato funkce představuje typické kód selhání. Výsledný výjimka zachycena ve funkci main nainstalované obslužná rutina výjimky celou aplikaci.

To lze provést pomocí vazby delegáta, kterého <xref:System.Windows.Forms.Application.ThreadException> událostí. V tomto případě následující výjimky jsou potom odeslány `App::OnUnhandled` metody.

## <a name="example"></a>Příklad

```
// global_exception_handler.cpp
// compile with: /clr
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Drawing;
using namespace System::Windows::Forms;

ref class MyForm : public Form
{
   Button^ b;
public:
   MyForm( )
   {
      b = gcnew Button( );
      b->Text = "Do Null Access";
      b->Size = Drawing::Size(150, 30);
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);
      Controls->Add(b);
   }
   void OnClick(Object^ sender, EventArgs^ args)
   {
      // do something illegal, like call through a null pointer...
      Object^ o = nullptr;
      o->ToString( );
   }
};

ref class App
{
public:
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)
   {
      MessageBox::Show(e->Exception->Message, "Global Exeception");
      Application::ExitThread( );
   }
};

int main()
{
   Application::ThreadException += gcnew
      ThreadExceptionEventHandler(App::OnUnhandled);

   MyForm^ form = gcnew MyForm( );
   Application::Run(form);
}
```

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../windows/exception-handling-cpp-component-extensions.md)