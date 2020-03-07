---
title: 'complex_modifications manipulator definition'
weight: 500
---

```text
      <section>
        <div class="page-header">
          <h1 id="complex_modifications-manipulator-definition"></h1>
        </div>

        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>type</code></td>
              <td><code class="required">required</code></td>
              <td>Always <code>"type": "basic"</code></td>
            </tr>
            <tr>
              <td><code>from</code></td>
              <td><code class="required">required</code></td>
              <td>
                The name of key code, consumer key code or pointing button which you want to change.
                <a href="#from-event-definition">(detail)</a>
              </td>
            </tr>
            <tr>
              <td><code>to</code></td>
              <td><code class="optional">optional</code></td>
              <td>events which are sent when you press <code>from</code> key.</td>
            </tr>
            <tr>
              <td><code>to_if_alone</code></td>
              <td><code class="optional">optional</code></td>
              <td>events which are sent when you press <code>from</code> key alone.</td>
            </tr>
            <tr>
              <td><code>to_if_held_down</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                events which are sent when you hold down <code>from</code> key.
              </td>
            </tr>
            <tr>
              <td><code>to_after_key_up</code></td>
              <td><code class="optional">optional</code></td>
              <td>events which are sent after you release <code>from</code> key.</td>
            </tr>
            <tr>
              <td><code>to_delayed_action</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <code>to_delayed_action</code> sends <code>to_delayed_action &gt; to_if_invoked</code> events after 500 milliseconds at you press <code>from</code> key.<br />
                <code>to_delayed_action &gt; to_if_canceled</code> events are sent if you press another key between <code>from</code> key and to_delayed_action invoked. (<code>to_if_invoked</code> events are not sent if <code>to_if_canceled</code> events are sent.)
              </td>
            </tr>
            <tr>
              <td><code>description</code></td>
              <td><code class="optional">optional</code></td>
              <td>A manipulator description for human.</td>
            </tr>
            <tr>
              <td><code>conditions</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Manipulator is applied only if condition is matched. (The frontmost application, device, etc.)
              </td>
            </tr>
            <tr>
              <td><code>parameters</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Override parameters such as <code>to_delayed_action_delay_milliseconds</code>.
              </td>
            </tr>
          </tbody>
        </table>

        {{! ================================================================================ }}

        <h2 id="from-event-definition">from event definition</h2>

```

## from event definition

```json
{
    "key_code": "The name of key_code",
    "consumer_key_code": "The name of consumer_key_code",
    "pointing_button": "The name of pointing_button",
    "any": "key_code or consumer_key_code or pointing_button",

    "modifiers": {
        "mandatory": [
            modifier,
            modifier,
            ...
        ],
        "optional": [
            modifier,
            modifier,
            ...
        ]
    },

    "simultaneous": [
        {
            "key_code, consumer_key_code, pointing_button or any"
        },
        {
            "key_code, consumer_key_code, pointing_button or any"
        },
        ...
    ],
    "simultaneous_options": {
        "detect_key_down_uninterruptedly": false,
        "key_down_order": "A restriction of input events order",
        "key_up_order": "A restriction of input events order",
        "key_up_when": "When key_up events are posted",
        "to_after_key_up": [
            to event definition,
            to event definition,
            ...
        ]
    }
}
```

```text
        <div class="alert alert-info" role="alert">
          <p>
            Note:<br />
            <code>key_code</code>, <code>consumer_key_code</code>, <code>pointing_button</code> and <code>any</code>
            are exclusive.
            You can specify one of them.
          </p>
        </div>

        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>key_code</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <a href="document.html#eventviewer">You can find key_code by EventViewer.</a>
                <a href="https://github.com/pqrs-org/Karabiner-Elements/blob/master/src/apps/PreferencesWindow/Resources/simple_modifications.json">(list)</a>
              </td>
            </tr>
            <tr>
              <td><code>consumer_key_code</code></td>
              <td><code class="optional">optional</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>pointing_button</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <div class="alert alert-warning" role="alert">
                  Caution:<br />
                  Be careful when manipulating <code>button1</code> to avoid losing the left click button.
                </div>
              </td>
            </tr>
            <tr>
              <td><code>any</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                You can use <code>any</code> as follows.<br />
                These matches all key codes, consumer key codes or pointing buttons.
                <ul>
                  <li><code>"any": "key_code"</code></li>
                  <li><code>"any": "consumer_key_code"</code></li>
                  <li><code>"any": "pointing_button"</code></li>
                </ul>

                <div class="alert alert-warning" role="alert">
                  Caution:<br />
                  Be careful when using <code>"any": "pointing_button"</code> to avoid losing the left click button.
                </div>
              </td>
            </tr>
            <tr>
              <td><code>modifiers</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Specify modifiers. (e.g., "change control-h to delete")
                <a href="#from-event-definition-modifiers">(detail)</a>
              </td>
            </tr>
            <tr>
              <td><code>simultaneous</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Specify multiple events which are pressed simultaneously.
                <a href="#simultaneous">(detail)</a>
              </td>
            </tr>
            <tr>
              <td><code>simultaneous_options</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Options for <code>simultaneous</code>.
                <a href="#simultaneous-options">(detail)</a>
              </td>
            </tr>
          </tbody>
        </table>

        <div id="raw-number-key-code">
          <div class="alert alert-info" role="alert">
            <p>
              Tips:<br/>
              You can also specify <code>key_code</code>, <code>consumer_key_code</code>, <code>pointing_button</code> with raw number as follows.<br/>
              (Do not add double quotes to the number!)
            </p>

```

```json
{
    "from": {
        "key_code": 41
    },
    ...
}
```

```text
        <hr class="horizontal-separator thin" />

        <h3 id="from-event-definition-modifiers">modifiers in from event definition</h3>

        <code>modifiers</code> works as follows.

        <table class="table">
          <tbody>
            <tr>
              <th>When <code>modifiers</code> is omitted</th>
              <td>
                Events are manipulated only if modifier keys are not pressed.
              </td>
            </tr>
            <tr>
              <th>When <code>modifiers &gt; mandatory</code> is specified</th>
              <td>
                Events are manipulated if mandatory modifiers are pressed. <br />
                Mandatory modifiers are omitted from <code>to events</code>.
              </td>
            </tr>
            <tr>
              <th>When <code>modifiers &gt; optional</code> is specified</th>
              <td>
                Events are also manipulated even if optional modifiers are pressed.<br />
                Optional modifiers are kept in <code>to events</code>.
              </td>
            </tr>
          </tbody>
        </table>

        <hr class="horizontal-separator thin" />

        <h3 id="from-event-definition-examples">Examples</h3>

        <div class="panel panel-default">
          <div class="panel-body">
            <p>Change escape to tab without <code>modifiers</code></p>
```

```json
{
    "type": "basic",
    "from": {
        "key_code": "escape"
    },
    "to": [
        {
            "key_code": "tab"
        }
    ]
}
```

```text
            <table class="table">
              <thead>
                <tr>
                  <th>key</th>
                  <th>manipulated</th>
                  <th>result</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>escape</td>
                  <td><b>manipulated</b></td>
                  <td>tab</td>
                </tr>
                <tr>
                  <td>left_shift + escape</td>
                  <td>not manipulated</td>
                  <td>left_shift + escape</td>
                </tr>
                <tr>
                  <td>left_control + escape</td>
                  <td>not manipulated</td>
                  <td>left_control + escape</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>

        <div class="panel panel-default">
          <div class="panel-body">
            <p>Change escape to tab with <code>optional modifiers</code></p>
```

```json
{
    "type": "basic",
    "from": {
        "key_code": "escape",
        "modifiers": {
            "optional": ["left_shift", "left_control"]
        }
    },
    "to": [
        {
            "key_code": "tab"
        }
    ]
}
```

```text
            <table class="table">
              <thead>
                <tr>
                  <th>key</th>
                  <th>manipulated</th>
                  <th>result</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>escape</td>
                  <td><b>manipulated</b></td>
                  <td>tab</td>
                </tr>
                <tr>
                  <td>left_shift + escape</td>
                  <td><b>manipulated</b></td>
                  <td>left_shift + tab</td>
                </tr>
                <tr>
                  <td>left_control + escape</td>
                  <td><b>manipulated</b></td>
                  <td>left_control + tab</td>
                </tr>
                <tr>
                  <td>left_option + escape</td>
                  <td>not manipulated</td>
                  <td>left_option + escape</td>
                </tr>
                <tr>
                  <td>left_shift + left_option + escape</td>
                  <td>not manipulated</td>
                  <td>
                    left_shift + left_option + escape<br />
                    (because left_option is not in optional modifiers)
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>

        <div class="panel panel-default">
          <div class="panel-body">
            <p>Change control-h to delete without <code>optional modifiers</code></p>

```

```json
{
    "type": "basic",
    "from": {
        "key_code": "h",
        "modifiers": {
            "mandatory": ["control"]
        }
    },
    "to": [
        {
            "key_code": "delete_or_backspace"
        }
    ]
}
```

```text
            <table class="table">
              <thead>
                <tr>
                  <th>key</th>
                  <th>manipulated</th>
                  <th>result</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>h</td>
                  <td>not manipulated</td>
                  <td>h</td>
                </tr>
                <tr>
                  <td>left_control + h</td>
                  <td><b>manipulated</b></td>
                  <td>delete_or_backspace</td>
                </tr>
                <tr>
                  <td>left_control + left_option + h</td>
                  <td>not manipulated</td>
                  <td>
                    left_control + left_option + h<br />
                    (because left_option is not in optional modifiers)
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>

        <div class="panel panel-default">
          <div class="panel-body">
            <p>Change control-h to delete with <code>optional modifiers</code></p>
```

```json
{
    "type": "basic",
    "from": {
        "key_code": "h",
        "modifiers": {
            "mandatory": ["control"],
            "optional": ["caps_lock", "option"]
        }
    },
    "to": [
        {
            "key_code": "delete_or_backspace"
        }
    ]
}
```

```text
            <table class="table">
              <thead>
                <tr>
                  <th>key</th>
                  <th>manipulated</th>
                  <th>result</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>h</td>
                  <td>not manipulated</td>
                  <td>h</td>
                </tr>
                <tr>
                  <td>left_control + h</td>
                  <td><b>manipulated</b></td>
                  <td>delete_or_backspace</td>
                </tr>
                <tr>
                  <td>left_control + left_option + h</td>
                  <td><b>manipulated</b></td>
                  <td>left_option + delete_or_backspace</td>
                </tr>
                <tr>
                  <td>left_control + left_shift + h</td>
                  <td>not manipulated</td>
                  <td>
                    left_control + left_shift + h<br />
                    (because left_shift is not in optional modifiers)
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>

        <hr class="horizontal-separator thin" />

        <h3 id="from-event-definition-modifiers-list">The list of modifiers in from definition</h3>

        <table class="table">
          <thead>
            <tr>
              <th>name</th>
              <th>description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>caps_lock</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>left_command</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>left_control</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>left_option</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>left_shift</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>right_command</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>right_control</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>right_option</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>right_shift</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>fn</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>command</code></td>
              <td>left command or right command</td>
            </tr>
            <tr>
              <td><code>control</code></td>
              <td>left control or right control</td>
            </tr>
            <tr>
              <td><code>option</code></td>
              <td>left option or right option</td>
            </tr>
            <tr>
              <td><code>shift</code></td>
              <td>left shift or right shift</td>
            </tr>
            <tr>
              <td><code>left_alt</code></td>
              <td>Alias of left_option (available since Karabiner-Elements 12.3.0)</td>
            </tr>
            <tr>
              <td><code>left_gui</code></td>
              <td>Alias of left_command (available since Karabiner-Elements 12.3.0)</td>
            </tr>
            <tr>
              <td><code>right_alt</code></td>
              <td>Alias of right_option (available since Karabiner-Elements 12.3.0)</td>
            </tr>
            <tr>
              <td><code>right_gui</code></td>
              <td>Alias of right_command (available since Karabiner-Elements 12.3.0)</td>
            </tr>
            <tr>
              <td><code>any</code></td>
              <td>any modifiers</td>
            </tr>
          </tbody>
        </table>

        {{! ================================================================================ }}

        <hr class="horizontal-separator thin" />

        <h3 id="simultaneous">Detail of <code>simultaneous</code></h3>

        <p>
          <code>simultaneous</code> manipulates keys which are pressed simultaneously in 50 milliseconds.
        </p>

        <h4 id="simultaneous-threshold-milliseconds">About threshold milliseconds</h4>

        <p>
          You can adjust threshold on <b>Preferences &gt; Complex Modifications &gt; Parameters</b>.
        </p>

        <div class="row">
          <div class="col-lg-4">
            {{#lightbox}}
              img/karabiner-elements-simultaneous_threshold_milliseconds@2x.png simultaneous_threshold_milliseconds
            {{/lightbox}}
          </div>
        </div>

        <p>
          It is same as adjusting <code>basic.simultaneous_threshold_milliseconds</code> parameter in json.
        </p>

        <h4 id="simultaneous-manipulation">About manipulation</h4>

        <p>
          There are some cases <code>simultaneous</code> does not modify events.
        </p>

        <ul>
          <li><code>simultaneous</code> does not modify events if any <b>from events</b> are released before all <b>from events</b> are pressed.</li>
          <li><code>simultaneous</code> does not modify events if <b>from events</b> are interrupted by another event.</li>
        </ul>

        <p>
          For example, changing <b>a</b>+<b>s</b>+<b>d</b> to <b>mission_control</b> works as the following table.
        </p>

        <table class="table">
          <thead>
            <tr>
              <th>Input</th>
              <th>Output</th>
              <th>Note</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <ol>
                  <li><b>a</b> key_down</li>
                  <li><b>s</b> key_down</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <ol>
                  <li><b>mission_control</b></li>
                </ol>
              </td>
              <td>
                <span class="glyphicon glyphicon-ok"></span> Manipulated.
              </td>
            </tr>
            <tr>
              <td>
                <ol>
                  <li><b>s</b> key_down</li>
                  <li><b>a</b> key_down</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <ol>
                  <li><b>mission_control</b></li>
                </ol>
              </td>
              <td>
                <span class="glyphicon glyphicon-ok"></span> Manipulated.<br />
                The key order is insensitive.
              </td>
            </tr>
            <tr>
              <td>
                <ol>
                  <li><b>a</b> key_down</li>
                  <li><b>s</b> key_down</li>
                  <li><b>a</b> key_up</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <ol>
                  <li><b>a</b> key_down</li>
                  <li><b>s</b> key_down</li>
                  <li><b>a</b> key_up</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <span class="glyphicon glyphicon-remove"></span> Not manipulated.<br />
                <b>a</b> is released before all input events are pressed.
              </td>
            </tr>
            <tr>
              <td>
                <ol>
                  <li><b>a</b> key_down</li>
                  <li><b>s</b> key_down</li>
                  <li><b>f</b> key_down</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <ol>
                  <li><b>a</b> key_down</li>
                  <li><b>s</b> key_down</li>
                  <li><b>f</b> key_down</li>
                  <li><b>d</b> key_down</li>
                </ol>
              </td>
              <td>
                <span class="glyphicon glyphicon-remove"></span> Not manipulated.<br />
                Another key (<b>f</b>) is pressed before all input events are pressed.
              </td>
            </tr>
          </tbody>
        </table>

        <p>
          Note: The manipulator definition of changing <b>a</b>+<b>s</b>+<b>d</b> to <b>mission_control</b>.
        </p>
```

```json
{
    "type": "basic",
    "from": {
        "simultaneous": [
            {
                "key_code": "a"
            },
            {
                "key_code": "s"
            },
            {
                "key_code": "d"
            }
        ],
        "modifiers": {
            "optional": ["any"]
        }
    },
    "to": [
        {
            "key_code": "mission_control"
        }
    ]
}
```

```text
        <h4 id="simultaneous-key-up">About key_up</h4>

        <p>
          The key_up event is posted when you release any <b>from events</b>.
        </p>

        <p>
          For example, changing <b>tab</b>+<b>q</b> to <b>mission_control</b> works as the following table.
        </p>

        <table class="table">
          <thead>
            <tr>
              <th>Input</th>
              <th>Output</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <b>tab</b> key_down
              </td>
              <td>
                ---
              </td>
            </tr>
            <tr>
              <td>
                <b>q</b> key_down
              </td>
              <td>
                <b>mission_control</b> key_down
              </td>
            </tr>
            <tr>
              <td>
                <b>tab</b> key_up
              </td>
              <td>
                <b>mission_control</b> key_up
              </td>
            </tr>
            <tr>
              <td>
                <b>q</b> key_up
              </td>
              <td>
                ---
              </td>
            </tr>
          </tbody>
        </table>

        <h4 id="simultaneous-options">About <code>simultaneous_options</code></h4>

        <p>
          There are some options for <code>simultaneous</code>.
        </p>

        <table class="table">
          <thead>
            <tr>
              <th>Key</th>
              <th>Description</th>
              <th>Value</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <code>detect_key_down_uninterruptedly</code>
              </td>
              <td>
                Specify whether key_down detection is interrupted with unrelated events.
              </td>
              <td>
                <code>true</code> or <code>false</code>
              </td>
            </tr>
            <tr>
              <td>
                <code>key_down_order</code>
              </td>
              <td>
                Restriction of key_down order.
              </td>
              <td>
                <code>insensitive</code>, <code>strict</code> or <code>strict_inverse</code>
              </td>
            </tr>
            <tr>
              <td>
                <code>key_up_order</code>
              </td>
              <td>
                Restriction of key_up order.
              </td>
              <td>
                <code>insensitive</code>, <code>strict</code> or <code>strict_inverse</code>
              </td>
            </tr>
            <tr>
              <td>
                <code>key_up_when</code>
              </td>
              <td>
                When key_up events are posted.
              </td>
              <td>
                <code>any</code> or <code>all</code>
              </td>
            </tr>
            <tr>
              <td>
                <code>to_after_key_up</code>
              </td>
              <td>
                events will be posted when all <b>from events</b> are released.
              </td>
              <td>
                An array of <b>to event definitions</b>.
              </td>
            </tr>
          </tbody>
        </table>

        <h4 id="simultaneous-options-key-down-order">About <code>simultaneous_options</code> &gt; <code>key_down_order</code></h4>

        <p>
          <code>simultaneous</code> checks the order of key_down events
          if <code>key_down_order</code> is specified and is not <code>insensitive</code>.
        </p>

        <p>
          For example, this definition manipulates <b>tab,q</b> to <b>mission_control</b> and
          does not manipulate <b>q,tab</b> events.
        </p>
```

```json
{
    "type": "basic",
    "from": {
        "simultaneous": [
            {
                "key_code": "tab"
            },
            {
                "key_code": "q"
            }
        ],
        "simultaneous_options": {
            "key_down_order": "strict"
        },
        "modifiers": {
            "optional": ["any"]
        }
    },
    "to": [
        {
            "key_code": "mission_control"
        }
    ]
}
```

```text
        <h4 id="simultaneous-options-key-up-order">About <code>simultaneous_options</code> &gt; <code>key_up_order</code></h4>

        <p>
          <code>simultaneous</code> checks the order of key_up events
          if <code>key_up_order</code> is specified and is not <code>insensitive</code>.
        </p>

        <div class="alert alert-info" role="alert">
          <h5>Note:</h5>
          <p><code>key_up_order</code> is ignored if <code>simultaneous_threshold_milliseconds</code> is reached.</p>
        </div>

        <p>
          For example, this definition manipulates <b>tab,q</b> to <b>mission_control</b> if the <b>tab</b> key is released before the <b>q</b> key within 500 milliseconds.<br />
          (You should set a large value to <code>simultaneous_threshold_milliseconds</code> when you use <code>key_up_order</code>.)
        </p>

        <table class="table">
          <thead>
            <tr>
              <th>Input</th>
              <th>Output</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <b>tab</b> &amp; <b>q</b> key_down
              </td>
              <td>
                ---
              </td>
            </tr>
            <tr>
              <td>
                <b>tab</b> key_up
              </td>
              <td>
                <p>
                  <b>mission_control</b> key_down<br />
                  <b>mission_control</b> key_up
                </p>

                <span class="label label-info">NOTE</span> Events will be posted just before <b>the last from event's key_up</b>.
              </td>
            </tr>
            <tr>
              <td>
                <b>q</b> key_up
              </td>
              <td>
                ---
              </td>
            </tr>
          </tbody>
        </table>
```

```json
{
    "type": "basic",
    "parameters": {
        "basic.simultaneous_threshold_milliseconds": 500
    },
    "from": {
        "simultaneous": [
            {
                "key_code": "tab"
            },
            {
                "key_code": "q"
            }
        ],
        "simultaneous_options": {
            "key_up_order": "strict"
        },
        "modifiers": {
            "optional": ["any"]
        }
    },
    "to": [
        {
            "key_code": "mission_control"
        }
    ]
}
```

```text
        <h4 id="simultaneous-options-key-up-when">About <code>simultaneous_options</code> &gt; <code>key_up_when</code></h4>

        Specify when key_up events are posted.

        <table class="table">
          <thead>
            <tr>
              <th>Value</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                <code>any</code>
              </td>
              <td>
                Post key_up events when any key is released.
              </td>
            </tr>
            <tr>
              <td>
                <code>all</code>
              </td>
              <td>
                Post key_up events when all keys are released.
              </td>
            </tr>
          </tbody>
        </table>


        <h4 id="simultaneous-options-key-up-order">About <code>simultaneous_options</code> &gt; <code>to_after_key_up</code></h4>

        <p><code>simultaneous_options</code> &gt; <code>to_after_key_up</code> will be posted when all <b>from events</b> are released.</p>

        <p>
          This feature is typically used to clear mode flag variables when all <b>from events</b> are released.
        </p>

        Example:<br />
        <ul>
          <li>
            <a href="https://github.com/pqrs-org/KE-complex_modifications/blob/master/docs/json/mouse_keys_mode_v4.json">Mouse Keys Mode v4 json</a>
            <ul>
              <li><a href="https://github.com/pqrs-org/KE-complex_modifications/blob/master/src/json/mouse_keys_mode_v4.json.rb">(json generator)</a></li>
              <li><a href="https://ke-complex-modifications.pqrs.org/#mouse_keys_mode_v4">(import)</a></li>
            </ul>
          </li>
        </ul>

        {{! ================================================================================ }}

        <hr class="horizontal-separator" />

        <h2 id="to-event-definition">to event definition</h2>
```

```json
{
    "key_code": "The name of key_code",
    "consumer_key_code": "The name of consumer_key_code",
    "pointing_button": "The name of pointing_button",

    "shell_command": "shell command",

    "select_input_source": {
        "language": "language regex",
        "input_source_id": "input source id regex",
        "input_mode_id": "input mode id regex"
    },

    "set_variable": {
        "name": "variable name",
        "value": "variable value"
    },

    "mouse_key": mouse_key definition,

    "modifiers": [
        modifier,
        modifier,
        ...
    ],

    "lazy": false,
    "repeat": true,
    "halt": false,
    "hold_down_milliseconds": 0
}
```

```text
        <div class="alert alert-info" role="alert">
          <p>
            Note:<br />
            <code>key_code</code>, <code>consumer_key_code</code>, <code>pointing_button</code>,
            <code>shell_command</code>, <code>select_input_source</code> and <code>set_variable</code>
            are exclusive.
            You can specify one of them.
          </p>
        </div>

        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>key_code</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <a href="document.html#eventviewer">You can find key_code by EventViewer.</a>
                <a href="https://github.com/pqrs-org/Karabiner-Elements/blob/master/src/apps/PreferencesWindow/Resources/simple_modifications.json">(list)</a>
              </td>
            </tr>
            <tr>
              <td><code>consumer_key_code</code></td>
              <td><code class="optional">optional</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>pointing_button</code></td>
              <td><code class="optional">optional</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>shell_command</code></td>
              <td><code class="optional">optional</code></td>
              <td></td>
            </tr>
            <tr>
              <td><code>select_input_source</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                You can find the current input source identifiers by <b>EventViewer &gt; Variables tab</b>.<br />
                <code>language</code>, <code>input_source_id</code> and <code>input_mode_id</code> are optional.
                <code>select_input_source</code> finds the input source by the specified regexs.
              </td>
            </tr>
            <tr>
              <td><code>set_variable</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Set internal variable value by <code>set_variable</code>.<br />
                It's designed to use with <code>variable_if</code> and <code>variable_unless</code> conditions.<br />
                You can confirm the current variables state in <b>EventViewer &gt; Variables tab</b>.
              </td>
            </tr>
            <tr>
              <td><code>mouse_key</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Move mouse pointer and scroll by <code>mouse_key</code>.<br />
                You can specify operations by combination of follows.<br />
                <ul>
                  <li><code>{ "x": speed }</code></li>
                  <li><code>{ "y": speed }</code></li>
                  <li><code>{ "vertical_wheel": speed }</code></li>
                  <li><code>{ "horizontal_wheel": speed }</code></li>
                  <li><code>{ "speed_multiplier": 1.0 }</code></li>
                </ul>

                Examples:<br />
                <ul>
                  <li>move left: <code>{ "mouse_key": { "x": -1536 } }</code></li>
                  <li>move right: <code>{ "mouse_key": { "x": 1536 } }</code></li>
                  <li>move up: <code>{ "mouse_key": { "y": -1536 } }</code></li>
                  <li>move down: <code>{ "mouse_key": { "y": 1536 } }</code></li>
                  <li>scroll left: <code>{ "mouse_key": { "horizontal_wheel": 32 } }</code></li>
                  <li>scroll right: <code>{ "mouse_key": { "horizontal_wheel": -32 } }</code></li>
                  <li>scroll up: <code>{ "mouse_key": { "vertical_wheel": -32 } }</code></li>
                  <li>scroll down: <code>{ "mouse_key": { "vertical_wheel": 32 } }</code></li>
                </ul>

                <ul>
                  <li>fast move left: <code>{ "mouse_key": { "x": -3072 } }</code></li>
                  <li>fast move right: <code>{ "mouse_key": { "x": 3072 } }</code></li>
                  <li>fast move up: <code>{ "mouse_key": { "y": -3072 } }</code></li>
                  <li>fast move down: <code>{ "mouse_key": { "y": 3072 } }</code></li>
                  <li>fast scroll left: <code>{ "mouse_key": { "horizontal_wheel": 64 } }</code></li>
                  <li>fast scroll right: <code>{ "mouse_key": { "horizontal_wheel": -64 } }</code></li>
                  <li>fast scroll up: <code>{ "mouse_key": { "vertical_wheel": -64 } }</code></li>
                  <li>fast scroll down: <code>{ "mouse_key": { "vertical_wheel": 64 } }</code></li>
                </ul>

                <ul>
                  <li>speed multiplier x2: <code>{ "mouse_key": { "speed_multiplier": 2.0 } }</code></li>
                  <li>speed multiplier /2: <code>{ "mouse_key": { "speed_multiplier": 0.5 } }</code></li>
                </ul>

                <div class="alert alert-info" role="alert">
                  Note:<br />
                  Speed and direction depend on <b>System Preferences &gt; Mouse</b> configuration.
                </div>
              </td>
            </tr>
            <tr>
              <td><code>modifiers</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                Specify modifiers.
              </td>
            </tr>
            <tr>
              <td><code>lazy</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <p>
                  <code>true</code> or <code>false</code>. The default value is <code>false</code>.
                </p>
                <p>
                  <code>lazy</code> parameter works with modifier. (e.g., <code>"key_code": "left_shift"</code>)<br />
                  When <code>"lazy": true</code>, the modifier works as the lazy modifier.<br />
                  The lazy modifier does not send own key events until another key is pressed together.
                </p>
              </td>
            </tr>
            <tr>
              <td><code>repeat</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <p>
                  <code>true</code> or <code>false</code>. The default value is <code>true</code>.
                </p>
                <p>
                  When <code>"repeat": false</code>, both <b>key_down</b> and <b>key_up</b> events are sent when you press the key.<br />
                  (When <code>"repeat": true</code>, <b>key_up</b> event is sent when you release the key.)
                </p>
                <p>
                  This behavior suppresses the key repeating when <code>"repeat": false</code>.
                </p>
                <div class="alert alert-info" role="alert">
                  Note:<br />
                  When you want to use <code>"repeat": false</code>, you have to set <code>repeat</code> in the last to event if you have multiple to events in a manipulator.
                </div>
              </td>
            </tr>
            <tr>
              <td><code>halt</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <p>
                  <code>true</code> or <code>false</code>. The default value is <code>false</code>.
                </p>
                <p>
                  The typical usage of <code>halt</code> is to cancel <code>to_after_key_up</code> if <code>to_if_alone</code> or <code>to_if_held_down</code> is triggered.
                </p>
                <p>
                  If <code>"halt": true</code> exists in <code>to_if_alone</code> or <code>to_if_held_down</code>, the <code>to_after_key_up</code> is suppressed when <code>to_if_alone</code> or <code>to_if_held_down</code> is triggered.
                </p>
                <p>
                  An example: <a target="_blank" href="https://github.com/pqrs-org/KE-complex_modifications/blob/master/docs/json/example_halt.json">https://github.com/pqrs-org/KE-complex_modifications/blob/master/docs/json/example_halt.json</a>
                </p>
              </td>
            </tr>
            <tr>
              <td><code>hold_down_milliseconds</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                <p>
                  An integer value. The default value is <code>0</code>.
                </p>
                <p>
                  Specify a key press period for when both key down and key up events are posted at the same time (e.g. <code>to_if_alone</code>)
                </p>
                <p>
                  Generally <code>hold_down_milliseconds</code> is used with <code>"key_code": "caps_lock"</code>.
                </p>
              </td>
            </tr>
          </tbody>
        </table>

        <hr class="horizontal-separator thin" />

        <h3 id="to-event-definition-modifiers-list">The list of modifiers in to definition</h3>

        <ul>
          <li><code>caps_lock</code></li>
          <li><code>left_command</code></li>
          <li><code>left_control</code></li>
          <li><code>left_option</code></li>
          <li><code>left_shift</code></li>
          <li><code>right_command</code></li>
          <li><code>right_control</code></li>
          <li><code>right_option</code></li>
          <li><code>right_shift</code></li>
          <li><code>fn</code></li>
        </ul>

        {{! ================================================================================ }}

        <hr class="horizontal-separator thin" />

        <h3 id="to-if-alone">Detail of <code>to_if_alone</code></h3>

        <p>
          <code>to_if_alone</code> posts events when the <b>from key</b> is pressed alone.<br />
          The events are posted at the <b>from key</b> is released.
        </p>

        <h4 id="to-if-alone-cancellation">About cancellation</h4>

        <p>
          <code>to_if_alone</code> is canceled if other events (keys, buttons or scroll wheel) is happen while the <b>from key</b> is pressed down.
        </p>
        <p>
          The cancellation also happens when you press <b>from key</b> long. (The default timeout is 1000 milliseconds.)<br />
          You can adjust the timeout milliseconds by <code>parameters &gt; basic.to_if_alone_timeout_milliseconds</code>.<br />
          The following examples set the timeout 500 milliseconds.
        </p>
```

```json
{
    "from": ...,
    "to": ...,
    "to_if_alone": [
        {
            "key_code": "escape"
        }
    ],
    "parameters": {
        "basic.to_if_alone_timeout_milliseconds": 500
    },
    "type": "basic"
}
```

```text
        <h4 id="to-if-alone-keyboard-repeat">About keyboard repeat</h4>

        <p>
          <code>to_if_alone</code> posts both <b>key_down</b> and <b>key_up</b> events at the same time.<br />
          Thus, you cannot use key repeat for <code>to_if_alone</code> events.
        </p>

        {{! ================================================================================ }}

        <hr class="horizontal-separator thin" />

        <h3 id="to-if-held-down">Detail of <code>to_if_held_down</code></h3>

        <p>
          <code>to_if_held_down</code> posts events when the <b>from key</b> is held down.<br />
        </p>

        <p>
          If <code>to</code> events are specified, <code>to</code> events are released before <code>to_if_held_down</code> are posted.
        </p>

        {{! ================================================================================ }}

        <hr class="horizontal-separator" />

        <h2 id="condition-definition">condition definition</h2>

        <h3 id="condition-definition-frontmost-application"><code>frontmost_application_if</code> and <code>frontmost_application_unless</code></h3>
```

```json
{
    "type": "frontmost_application_if",
    "bundle_identifiers": [
        bundle identifier regex,
        bundle identifier regex,
        ...
    ],
    "file_paths": [
        file path regex,
        file path regex,
        ...
    ]
}
```

```text
        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>type</code></td>
              <td><code class="required">required</code></td>
              <td>
                Either:
                <ul>
                  <li><code>"type": "frontmost_application_if"</code></li>
                  <li><code>"type": "frontmost_application_unless"</code></li>
                </ul>
              </td>
            </tr>
            <tr>
              <td><code>bundle_identifiers</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                bundle identifier regexs.<br />
                You can examine application's bundle identifier in <b>EventViewer &gt; Frontmost Application tab</b>.
              </td>
            </tr>
            <tr>
              <td><code>file_paths</code></td>
              <td><code class="optional">optional</code></td>
              <td>
                file path regexs.<br />
                You can examine application's file path in <b>EventViewer &gt; Frontmost Application tab</b>.
              </td>
            </tr>
            <tr>
              <td><code>description</code></td>
              <td><code class="optional">optional</code></td>
              <td>A condition description for human.</td>
            </tr>
          </tbody>
        </table>

        <hr class="horizontal-separator thin" />

        <h3 id="condition-definition-device"><code>device_if</code> and <code>device_unless</code></h3>
```

```json
{
    "type": "device_if",
    "identifiers": [
        {
            "vendor_id": 1111,
            "product_id": 2222,
            "description": "my keyboard 1"
        },
        {
            "vendor_id": 3333,
            "product_id": 4444,
            "description": "my keyboard 2"
        },
        ...
    ]
}
```

```text
        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>type</code></td>
              <td><code class="required">required</code></td>
              <td>
                Either:
                <ul>
                  <li><code>"type": "device_if"</code></li>
                  <li><code>"type": "device_unless"</code></li>
                </ul>
              </td>
            </tr>
            <tr>
              <td><code>identifiers</code></td>
              <td><code class="required">required</code></td>
              <td>
                <p>
                  Target device designation by the following identifiers.<br />
                  You can examine them in <b>EventViewer &gt; Devices tab</b>.
                </p>

                <ul>
                  <li><code>vendor_id</code></li>
                  <li><code>product_id</code></li>
                  <li><code>location_id</code></li>
                  <li><code>is_keyboard</code></li>
                  <li><code>is_pointing_device</code></li>
                </ul>

                <p>
                  All identifiers are optional.
                </p>
              </td>
            </tr>
            <tr>
              <td><code>description</code></td>
              <td><code class="optional">optional</code></td>
              <td>A condition description for human.</td>
            </tr>
          </tbody>
        </table>

        <hr class="horizontal-separator thin" />

        <h3 id="condition-definition-keyboard-type"><code>keyboard_type_if</code> and <code>keyboard_type_unless</code></h3>
```

```json
{
    "type": "keyboard_type_if",
    "keyboard_types": ["ansi", "iso"]
}
```

```text
        <div class="alert alert-info" role="alert">
          It's useful for supporting "change control-[ to escape" with all keyboard types.
          <a target="_blank" href="https://github.com/pqrs-org/KE-complex_modifications/blob/master/docs/json/example_keyboard_type.json">(example json)</a><br />
          Some characters have different key code for each keyboard types.<br />
          (e,g,. <b>[</b> is <code>open_bracket</code> on <b>ansi</b> and <b>iso</b>, <code>close_bracket</code> on <b>jis</b>.)
        </div>

        <table class="table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Required</th>
              <th>Description</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><code>type</code></td>
              <td><code class="required">required</code></td>
              <td>
                Either:
                <ul>
                  <li><code>"type": "keyboard_type_if"</code></li>
                  <li><code>"type": "keyboard_type_unless"</code></li>
                </ul>
              </td>
            </tr>
            <tr>
              <td><code>keyboard_types</code></td>
              <td><code class="required">required</code></td>
              <td>
                Target keyboard types.
                <ul>
                  <li><code>ansi</code></li>
                  <li><code>iso</code></li>
                  <li><code>jis</code></li>
                </ul>
              </td>
            </tr>
            <tr>
              <td><code>description</code></td>
              <td><code class="optional">optional</code></td>
              <td>A condition description for human.</td>
            </tr>
          </tbody>
        </table>

        <hr class="horizontal-separator thin" />
```

-   [`input_source_if`, `input_source_unless`](conditions/input-source/)
-   [`variable_if`, `variable_unless`](conditions/variable/)
-   [`event_changed_if`, `event_changed_unless`](conditions/event-changed/)