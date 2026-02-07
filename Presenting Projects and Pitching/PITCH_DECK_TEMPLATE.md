# Pitch Deck Template

A slide-by-slide template for presenting technical projects. Adapt this structure to your specific project and audience.

---

## Overview

**Total slides:** 8-12 slides  
**Total time:** 5-10 minutes (adjust based on your time limit)  
**Rule of thumb:** ~1 minute per slide

---

## Slide 1: Title Slide

**Purpose:** Introduce your project and team.

**Include:**
- Project name
- One-line description or tagline
- Your name(s)
- Date/event name
- (Optional) Logo or hero image

**Example:**
```
ParkSmart
Real-time parking availability prediction

Jane Doe & John Smith
AIC x GDGC Tech Tournament 2026
```

**Time:** 15-30 seconds

---

## Slide 2: The Problem

**Purpose:** Make the audience feel the pain you're solving.

**Include:**
- Clear statement of the problem
- Who has this problem (target users)
- Why it matters (impact, frequency, cost)
- (Optional) A statistic or quote

**Example:**
```
The Problem

Drivers spend an average of 17 hours per year looking for parking.

• 30% of urban traffic is people circling for spots
• Leads to frustration, wasted time, and pollution
• Existing apps show garages, not street parking
```

**Tips:**
- Be specific and concrete
- Make it relatable
- Don't jump to the solution yet

**Time:** 1-2 minutes

---

## Slide 3: The Solution

**Purpose:** Introduce what you built at a high level.

**Include:**
- One sentence describing your solution
- How it addresses the problem
- Key differentiator (what makes your approach unique)
- Screenshot or mockup of the product

**Example:**
```
Our Solution

ParkSmart predicts street parking availability using 
real-time traffic data and machine learning.

• Shows probability of finding parking by block
• Updates every 5 minutes
• Works for street parking, not just garages
```

**Tips:**
- Keep it high-level — details come later
- Include a visual (screenshot, diagram, mockup)
- Connect directly back to the problem

**Time:** 1-2 minutes

---

## Slide 4: Demo (or Screenshots)

**Purpose:** Show your project in action.

**Options:**
- **Live demo** — If you're confident and have backups
- **Video recording** — Safer, can be edited
- **Screenshots with narration** — Most reliable

**Include:**
- 2-4 key screens or interactions
- Annotations highlighting important features
- Narration of user flow

**Tips:**
- Show the happy path (it works!)
- Use realistic-looking data
- Keep it short (1-2 minutes)
- Have a backup ready

**Time:** 1-3 minutes

---

## Slide 5: How It Works (Architecture)

**Purpose:** Explain the technical approach.

**Include:**
- High-level architecture diagram
- Key technologies used
- Data flow (input → processing → output)

**Example diagram:**
```
[User App] → [API Server] → [ML Model] → [Prediction]
                 ↓
            [Database]
                 ↑
         [Traffic Data Feed]
```

**Tips:**
- Match detail level to your audience
- Use a diagram — don't just list technologies
- Explain WHY you made key technical choices

**Time:** 1-2 minutes

---

## Slide 6: Technical Deep Dive (Optional)

**Purpose:** Go deeper on an interesting technical challenge.

**Include:**
- A specific problem you faced
- How you solved it
- Code snippet, algorithm, or diagram
- Results of your approach

**Example:**
```
Challenge: Real-Time Predictions

Problem: Needed predictions in <100ms for good UX

Solution:
• Pre-computed predictions for common scenarios
• Cached results with 5-minute TTL
• Async model updates in background

Result: Average response time of 45ms
```

**Tips:**
- Pick the most interesting or challenging part
- This is where you show technical depth
- Skip this slide for non-technical audiences

**Time:** 1-2 minutes

---

## Slide 7: Results & Impact

**Purpose:** Show that your project works and matters.

**Include:**
- Metrics (accuracy, speed, user count, etc.)
- User feedback or testimonials
- Comparison to alternatives (if applicable)
- Visualizations of results

**Example:**
```
Results

Model Performance:
• 78% accuracy predicting parking availability
• Tested on 10,000 historical data points

User Testing:
• 15 beta users over 2 weeks
• "Saved me 10 minutes finding parking" — Beta User

Compared to guessing: 23% improvement
```

**Tips:**
- Use concrete numbers
- Be honest about limitations
- Show you measured success

**Time:** 1 minute

---

## Slide 8: Challenges & Learnings

**Purpose:** Show self-awareness and growth.

**Include:**
- 2-3 challenges you faced
- How you overcame them (or tried to)
- What you learned
- What you'd do differently

**Example:**
```
Challenges & Learnings

Challenges:
• Limited training data for our specific city
• Real-time API rate limits

What We Learned:
• Data augmentation helped with limited data
• Caching is essential for real-time apps
• Start with a simpler model first

What We'd Do Differently:
• More user testing earlier
• Build data collection into MVP
```

**Tips:**
- Being honest about challenges shows maturity
- Focus on what you learned, not just what went wrong
- This is often asked in Q&A — address it proactively

**Time:** 1 minute

---

## Slide 9: Future Work (Optional)

**Purpose:** Show the project has potential beyond the current scope.

**Include:**
- Next features you'd build
- Scaling plans
- Potential applications
- What you'd need (time, data, resources)

**Example:**
```
What's Next

Short-term:
• Add more cities
• Integrate with Google Maps

Long-term:
• Partner with city parking authorities
• Add EV charging availability
• Explore B2B for delivery companies
```

**Tips:**
- Be realistic about scope
- Shows you're thinking ahead
- Can spark interesting Q&A

**Time:** 30-60 seconds

---

## Slide 10: Conclusion / Call to Action

**Purpose:** Leave a strong final impression.

**Include:**
- One-sentence summary of your project
- Key takeaway you want the audience to remember
- Call to action (try it, give feedback, contact info)
- Thank you

**Example:**
```
Summary

ParkSmart makes finding street parking less frustrating 
using ML-powered predictions.

Try it: parksmart-demo.vercel.app
GitHub: github.com/username/parksmart
Contact: jane@email.com

Thank you! Questions?
```

**Tips:**
- End with confidence
- Make it easy for people to follow up
- Don't end with "That's it" — end with something memorable

**Time:** 30 seconds

---

## Slide 11: Q&A

**Purpose:** Open the floor for questions.

**Include:**
- "Questions?" or "Let's Discuss"
- (Optional) Contact info again
- (Optional) Links to demo/repo

**Tips:**
- Have prepared answers for likely questions
- It's okay to say "I don't know, but I'd look into..."
- Keep answers concise

---

## Putting It All Together

### Slide Count by Section

| Section | Slides | Time |
|---------|--------|------|
| Title | 1 | 0:30 |
| Problem | 1 | 1:30 |
| Solution | 1 | 1:30 |
| Demo | 1 | 2:00 |
| How It Works | 1-2 | 2:00 |
| Results | 1 | 1:00 |
| Learnings | 1 | 1:00 |
| Future/Conclusion | 1-2 | 1:00 |
| **Total** | **8-11** | **~10 min** |

### Adjusting for Time

**5 minutes:** Cut Technical Deep Dive and Future Work  
**7 minutes:** Cut Future Work, shorten demo  
**10 minutes:** Use full template  
**15+ minutes:** Add more technical depth, expand Q&A

---

## Template Checklist

Before presenting, verify:

- [ ] Every slide has one clear purpose
- [ ] Slides are not text-heavy (use visuals)
- [ ] Demo/screenshots are ready and tested
- [ ] You've practiced with a timer
- [ ] You have backups for everything
- [ ] Contact info/links are correct
- [ ] Font is large enough to read from the back

---

## Quick Reference: Slide Titles

1. [Project Name]
2. The Problem
3. Our Solution
4. Demo
5. How It Works
6. Technical Deep Dive (optional)
7. Results
8. Challenges & Learnings
9. What's Next (optional)
10. Thank You / Questions
