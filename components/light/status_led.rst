Status LED Light
================

.. seo::
    :description: Instructions for setting up a Status LED shared also as binary ON/OFF light in ESPHome.
    :image: led-on.svg

The ``status_led`` light platform allows to share a single LED for indicating the status of
the device (when on error/warning state) or as binary light (when on OK state).
This is useful for devices with only one LED available.

It provides the combined functionality of :doc:`status_led component </components/status_led>` and a
:doc:`binary light component </components/light/binary>` over a single shared GPIO led.

When the device is on error/warning state, the function of ``status_led`` will take precedence and control the blinking of the LED.
When the device is in OK state, the LED will be restored to the state of the ``binary light`` function and can be controlled as such.

.. code-block:: yaml

    # Example configuration entry
    light:
      - platform: status_led
        name: "Switch state"
        pin: GPIO2

.. note::

    When using this platform the high level ``status_led`` component should not be included (at least over the same pin),
    as its functionality is directly provided by this platform.

    The only difference is that the platform won't be loaded in OTA safe mode, while the component would be.

Configuration variables:
------------------------

- **name** (**Required**, string): The name of the light.
- **pin** (**Required**, :ref:`Pin Schema <config-pin_schema>`): The GPIO pin to operate the LED on.
- **id** (*Optional*, :ref:`config-id`): Manually specify the ID used for code generation.
- **effects** (*Optional*, list): A list of :ref:`light effects <light-effects>` to use for this light, though binary lights
  only support very few of them.
- All other options from :ref:`Light <config-light>`.

See Also
--------

- :doc:`/components/status_led`
- :doc:`/components/light/binary`
- :doc:`/components/light/index`
- :apiref:`status_led/light/status_led_light.h`
- :ghedit:`Edit`
