---
layout: default
title: Internationalization
permalink: /integration/sdk/internationalization
nav_order: 2
parent: JavaScript SDK
grand_parent: Integration
---

# Internationalization (i18n)

We offer language for your verification form in a layered approach. The layers are:

1. SheerID default messages
1. Per-program (overrides "default")
1. Javascript Library (overrides "per-program" and "default")


## SheerID default messages
All of the words and phrases shown in our verification flows are offered in a variety of languages. You can see which messages are available in the REST API reference.

## Per-program overrides
Certain phrases can be customized in by editing your program in the [self-service tool](https://trial-preview.sheerid.com), using the Customize Experience step.

## Javascript Library overrides
You may specify messages when initializing your form using the `setOptions` method in Javscript.

    <script>
    sheerId.setOptions({
        messages: {
            'step.collectStudentPersonalInfo.title': 'Verify (js options override)'
        }
    });
    </script>

Note that all messages objects are flattened, so you can use a dot-string property or full objects:
    
    <script>
    sheerId.setOptions({
        messages: {
            // dot-string works
            'step.collectStudentPersonalInfo.title': 'Verify (js options override)',
            
            // object works too!
            step: {
                collectStudentPersonalInfo: {
                    subtitle: 'Verify Subtitle (js)',
                }
            }
        }
    });
    </script>

<a href="examples/language-override.html" target="_blank">See a live example here</a>
