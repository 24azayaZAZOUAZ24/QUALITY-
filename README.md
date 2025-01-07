# QUALITY-
from graphviz import Digraph

# Create a new directed graph
diagram = Digraph(format="png", graph_attr={"rankdir": "TB"}, name="ThreeLevelReviewSystem")

# Add nodes for each step in the process
diagram.node("Start", "Designer Completes Task", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("DesignerReview", "Designer Reviews Task", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("Proofreader", "Submit to Proofreader", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("Feedback", "Proofreader Checks Task", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("Modify", "Designer Modifies Task (if errors)", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("Reviewer", "Submit to Reviewer", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("Approval", "Submit to Approver", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("SpecialtyDirector", "Submit to Specialty Director", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("InternalPanel", "Internal Judges' Panel Review (Key Tasks)", shape="box", style="rounded,filled", fillcolor="lightblue")
diagram.node("ExternalReview", "Submit for External Review", shape="box", style="rounded,filled", fillcolor="lightblue")

# Add edges with directions
diagram.edge("Start", "DesignerReview")
diagram.edge("DesignerReview", "Proofreader")
diagram.edge("Proofreader", "Feedback")
diagram.edge("Feedback", "Modify", label="Errors Found")
diagram.edge("Modify", "Proofreader")
diagram.edge("Feedback", "Reviewer", label="No Errors")
diagram.edge("Reviewer", "Approval")
diagram.edge("Approval", "SpecialtyDirector")
diagram.edge("SpecialtyDirector", "InternalPanel", label="Key Tasks Only")
diagram.edge("SpecialtyDirector", "ExternalReview")

# Render the diagram
file_path = "/mnt/data/ThreeLevelReviewSystem.png"
diagram.render(file_path, format="png", cleanup=True)
file_path
