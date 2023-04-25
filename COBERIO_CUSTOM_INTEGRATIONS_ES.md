# COBERIO INTEGRACIONES CUSTOM

| RELEASE NUMBER | DESCRIPTION |
|----------------|----------|
| 1.0            | CASOS CUSTOM QUE NO SE INTEGRAN MEDIANTE UN PLUGIN ECOMMERCE         |---|---|---|

### Onboarding para clientes (clásico y con pasarela de pagos): 
    (GET) https://coberio.typeform.com/to/{store_form_id}#sku=xxx&campaign=yyy&ecommercesessionid=zzz
### Onboarding para clientes (Seguro gratuito que no precisa el pago del cliente) 
    (GET) https://coberio.typeform.com/to/{store_form_id}#sku=xxx&campaign=yyy&ecommercesessionid=zzz&custom1=kkk

Ambos Onboardings tienen un número de parámetros diferente:

- En el caso de Onboarding Clásico (con pasarela de pagos incluida) se pueden enviar tres parámetros (ninguno de ellos es obligatorio):
  - **sku**: sirve para identificar el código de unidad mínima de compra.
  - **campaign**: sirve para identificar una potencial campaña definida en el e-commerce. 
  - **ecommercesessionid**: sirve para identificar un shopping cart, sesión de usuario o cualquier identificador único que el e-commerce considere oportuno

    #### Ejemplo de onboarding clásico con pasarela de pagos:
        https://coberio.typeform.com/to/abcdefg#sku=piano123&campaign=may2023_pianos&ecommercesessionid=678-4355-75548-27464

- En el caso del Onboarding de seguro gratuito además de los incluidos en el caso clásico tendremos un parámetro más con caracter obligatorio:
  - **custom1**: este parámetro sirve para enviarnos cualquier número de parámetros específicos del comercio. 
    - Se ha establecido la obligatoriedad de incluir el parámetro “price” que sirve para enviar el precio del producto asegurado (no se le pedirá al cliente en el onboarding). 
  
    #### Ejemplo de onboarding de seguro gratuito:   
        https://coberio.typeform.com/to/abcdefg#sku=guitarra_espanola1&campaign=april2023_guitarras&ecommercesessionid=2342-3413-43535-45345&custom1=price:1000.05
        (* el parámetro price es un double con dos decimales)
  
### Algunas notas a tener en cuenta:
- El formato del parámetro "custom1" es:
    …&custom1=price:1000.05;key1:value1;key2:value2;…;keyN:valueN...
- Todos los parámetros de entrada al onboarding se almacenan durante la sesión de contratación de la poliza y son enviados de vuelta mediante un callback a un endpoint configurable (suministrado por el comercio). El request que se realiza en este callback se deberá ajustar a un verbo http GET.
