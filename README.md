### script overwrite
create_cadet_branch_decision
found_cadet_house_decision_effect

### decision added conditions
if clan:
    OR = {
        has_house_unity_stage = antagonistic
        has_house_unity_stage = competitive
        is_independent_ruler = yes
    }
if not(clan):
    OR = {
        NOT = { culture = { has_same_culture_heritage = { house_head.culture } } }
        culture = { cultural_acceptance = { target = house_head.culture value < 30 } }
        is_independent_ruler = yes
    }

highest_held_title_tier >= tier_duchy
prestige_level >= 3
legitimacy_level >= 3

if house_head.faith is astray or lower:
    legitimacy_level > house_head.legitimacy_level

# dicision added effect
if old_house_head.faith is evil or above:
    generate_coa = yes (no coa divided into four parts, yes completely new coa)