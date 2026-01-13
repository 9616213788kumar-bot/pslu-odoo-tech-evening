<?xml version="1.0" encoding="utf-8"?>
<odoo>

    <!-- FORM VIEW -->
    <record id="croissantage_event_view_form" model="ir.ui.view">
        <field name="name">croissantage.event.view.form</field>
        <field name="model">croissantage.event</field>
        <field name="arch" type="xml">
            <form>
                <header>

                    <!-- STATUS BAR -->
                    <field name="state"
                           widget="statusbar"
                           options="{'clickable': 1}"
                           groups="croissantage.group_croissantage_manager"/>

                    <!-- VALIDATE BUTTON -->
                    <button string="Validate"
                            name="act_validate"
                            type="object"
                            class="oe_highlight"
                            groups="croissantage.group_croissantage_manager"
                            attrs="{'invisible': [('state','=','done')]}"/>

                </header>

                <sheet>
                    <div class="oe_title">
                        <label for="name"/>
                        <h1>
                            <field name="name" placeholder="Event Name"/>
                        </h1>
                    </div>

                    <group>
                        <group>
                            <field name="croissanted_id"/>
                            <field name="city"/>
                            <field name="croissanter_ids" widget="many2many_tags"/>
                        </group>

                        <group>
                            <field name="date_start"/>
                            <field name="date_end"/>
                            <field name="duration"/>
                        </group>
                    </group>
                </sheet>

                <chatter/>
            </form>
        </field>
    </record>

    <!-- LIST VIEW -->
    <record id="croissantage_event_view_list" model="ir.ui.view">
        <field name="name">croissantage.event.view.list</field>
        <field name="model">croissantage.event</field>
        <field name="arch" type="xml">
            <tree>
                <field name="name"/>
                <field name="croissanted_id"/>
                <field name="croissanter_ids" widget="many2many_tags"/>
                <field name="state"/>
            </tree>
        </field>
    </record>

    <!-- ACTION -->
    <record id="croissantage_event_action" model="ir.actions.act_window">
        <field name="name">Croissantages</field>
        <field name="res_model">croissantage.event</field>
        <field name="view_mode">tree,form</field>
    </record>

    <!-- MENU -->
    <menuitem
        id="croissantage_menu"
        name="Croissantage"
        action="croissantage_event_action"
    />

</odoo>
